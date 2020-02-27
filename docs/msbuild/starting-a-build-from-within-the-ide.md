---
title: Uruchamianie kompilacji z poziomu środowiska IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8c4792590565c027a316ed95abb067faa30f5dc
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632124"
---
# <a name="start-a-build-from-within-the-ide"></a>Rozpocznij kompilację z poziomu środowiska IDE

Niestandardowe systemy projektów muszą używać <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> do uruchamiania kompilacji. W tym artykule opisano przyczyny tego wymagania i przedstawiono procedurę.

## <a name="parallel-builds-and-threads"></a>Kompilacje równoległe i wątki

 Program Visual Studio umożliwia kompilacje równoległe, które wymagają mediacji w celu uzyskania dostępu do typowych zasobów. Systemy projektów mogą uruchamiać kompilacje asynchronicznie, ale te systemy nie mogą wywoływać funkcji kompilacji z poziomu wywołań zwrotnych.

 Jeśli system projektu modyfikuje zmienne środowiskowe, musi ustawić NodeAffinity kompilacji na OutOfProc. To wymaganie oznacza, że nie można używać obiektów hosta, ponieważ wymagają węzła w procesie.

## <a name="use-ivsbuildmanageraccessor"></a>Use IVSBuildManagerAccessor

 Poniższy kod przedstawia metodę, którą system projektu może użyć do uruchomienia kompilacji:

```csharp

public bool Build(Project project, bool isDesignTimeBuild)
{
    // Get the accessor from the IServiceProvider interface for the
    // project system
    IVsBuildManagerAccessor accessor =
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as
        IVsBuildManagerAccessor;
    bool releaseUIThread = false;
    try
    {
        if(accessor != null)
        {
            // Claim the UI thread under the following conditions:
            // 1. The build must use a resource that uses the UI thread
            // or,
            // 2. The build requires the in-proc node AND waits on the
            // UI thread for the build to complete
            if(NeedsUIThread)
            {
                int result = accessor.ClaimUIThreadForBuild();
                if(result != S_OK)
                {
                     // Not allowed to claim the UI thread right now
                     return false;
                }
                releaseUIThread = true;
             }
             if(isDesignTimeBuild)
             {
// Start the design time build
                  int result = accessor.BeginDesignTimeBuild();
                  if(result != S_OK)
                  {
                      // Not allowed to begin a design-time build at
                      // this time. Try again later.
                      return false;
                  }
             }
         }
         bool buildSucceeded = false;
         // perform project-system specific build set up tasks
         // Create your BuildRequestData
         // This assumes a IHostServices variable (hostServices) set
   // to your host services. If you don't use a project instance
         // (you build from a file for example) then use another
         // constructor.
         BuildRequestData requestData = new
             BuildRequestData(project.CreateProjectInstance(),
             "myTarget", hostServices,
             BuildRequestData.BuildRequestDataFlags.None);
         // Mark your your submission as Pending
         BuildSubmission submission =
              BuildManager.DefaultBuildManager.
              PendBuildRequest(requestData);
         // Register the loggers in BuildLoggers
         if (accessor != null)
         {
               foreach (ILogger logger in BuildLoggers)
               {
                    accessor.RegisterLogger(submission.SubmissionId,
                        logger);
               }
         }
         BuildResult buildResult = submission.Execute();
         return buildResult;
     }
     // Clean up resources
     finally
     {
         if(accessor != null)
         {
             // Unregister the loggers, if necessary.
             accessor.UnregisterLoggers(submission.SubmissionId);
             // Release the UI thread, if used
             if(releaseUIThread)
             {
                  accessor.ReleaseUIThreadForBuild();
             }
             // End the design time build, if used
             if(isDesignTimeBuild)
             {
                  accessor.EndDesignTimeBuild();
             }
         }
     }
}
```
