---
title: AktualizacjaManifestForBrowserZadania aplikacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079eecd6751f168a7beba32eda6d15eda712bd7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631331"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserZachodźenie zadanie

Zadanie <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> jest uruchamiane w celu dodania ** \<hostInBrowser />** element do manifestu aplikacji (*\<projectname>.exe.manifest*) po zbudowaniu projektu aplikacji przeglądarki XAML (XBAP).

## <a name="task-parameters"></a>Parametry zadania

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationManifest`|Wymagany parametr **ITaskItem[].**<br /><br /> Określa ścieżkę i nazwę pliku manifestu aplikacji, `<hostInBrowser />` do którego chcesz dodać element.|
|`HostInBrowser`|Wymagany parametr **logiczny.**<br /><br /> Określa, czy zmodyfikować manifest aplikacji, aby uwzględnić ** \<hostInBrowser />** element. Jeśli **true**, nowy ** \<hostInBrowser />** element znajduje się w ** \<entryPoint />** element. Włączenie elementu jest kumulatywny: jeśli ** \<hostInBrowser />** element już istnieje, nie jest usuwany lub zastępowany. Zamiast tego tworzony jest dodatkowy ** \<hostInBrowser />** element. Jeśli **false**, manifest aplikacji nie jest modyfikowany.|

## <a name="remarks"></a>Uwagi

 XBAPs są uruchamiane przy użyciu clickonce wdrożenia, więc muszą być publikowane z obsługi wdrażania i manifestów aplikacji. MSBuild używa [generateApplicationManifest](generateapplicationmanifest-task.md) zadanie do generowania manifestu aplikacji.

 Następnie, aby skonfigurować aplikację, która ma być hostowana z przeglądarki, do manifestu aplikacji należy dodać dodatkowy ** \<hostInBrowser />** element, jak pokazano w poniższym przykładzie:

```xml
<!--MyXBAPApplication.exe.manifest-->
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly ... >
    <asmv1:assemblyIdentity ... />
    <application />
    <entryPoint>
      ...
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />
    </entryPoint>
  ...
/>
```

 Zadanie <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> jest uruchamiane, gdy projekt XBAP jest `<hostInBrowser />` zbudowany w celu dodania elementu.

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak `<hostInBrowser />` upewnić się, że element znajduje się w pliku manifestu aplikacji.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UpdateManifestForBrowserApplicationTask">
    <UpdateManifestForBrowserApplication
      ApplicationManifest="MyXBAPApplication.exe.manifest"
      HostInBrowser="true" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)