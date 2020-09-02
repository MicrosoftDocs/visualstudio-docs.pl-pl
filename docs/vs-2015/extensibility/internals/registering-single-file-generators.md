---
title: Rejestrowanie generatorów pojedynczych plików | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696101"
---
# <a name="registering-single-file-generators"></a>Rejestrowanie generatorów jednoplikowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby udostępnić niestandardowe narzędzie w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , należy je zarejestrować, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] można było je utworzyć i kojarzyć z określonym typem projektu.  
  
### <a name="to-register-a-custom-tool"></a>Aby zarejestrować narzędzie niestandardowe  
  
1. Zarejestruj bibliotekę DLL narzędzia niestandardowego w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rejestrze lokalnym lub w rejestrze systemowym w obszarze HKEY_CLASSES_ROOT.  
  
     Na przykład poniżej przedstawiono informacje o rejestracji zarządzanego narzędzia niestandardowego MSDataSetGenerator, które zawiera [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] :  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. Utwórz klucz rejestru w odpowiedniej gałęzi, w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obszarze Identyfikator GUID generatorów \\ *GUID* , gdzie *GUID* jest identyfikatorem GUID zdefiniowanym przez system lub usługę projektu określonego języka. Nazwa klucza jest programowaną nazwą narzędzia niestandardowego. Klucz niestandardowego narzędzia ma następujące wartości:  
  
    - (Domyślnie)  
  
         Opcjonalny. Zapewnia przyjazny dla użytkownika opis niestandardowego narzędzia. Ten parametr jest opcjonalny, ale zalecany.  
  
    - Identyfikator  
  
         Wymagany. Określa identyfikator biblioteki klas składnika COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  
  
    - GeneratesDesignTimeSource  
  
         Wymagany. Wskazuje, czy typy z plików utworzonych przez to narzędzie niestandardowe są udostępniane projektantom wizualizacji. Wartość tego parametru musi być równa (zero) 0 dla typów niedostępnych dla projektantów wizualizacji lub (jeden) 1 dla typów dostępnych dla projektantów wizualizacji.  
  
    > [!NOTE]
    > Narzędzie niestandardowe należy zarejestrować osobno dla każdego języka, dla którego ma być dostępne narzędzie niestandardowe.  
  
     Na przykład MSDataSetGenerator rejestruje się osobno dla każdego języka:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementowanie generatorów pojedynczych plików](../../extensibility/internals/implementing-single-file-generators.md)   
 [Określanie domyślnej przestrzeni nazw projektu](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Uwidacznianie typów dla projektantów wizualizacji](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Wprowadzenie do obiektu BuildManager](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
