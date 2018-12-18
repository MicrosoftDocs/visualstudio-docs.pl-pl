---
title: Rejestrowanie generatorów jednoplikowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e601b3fcf8bd702c1bc6cde427766d0f107e6bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780987"
---
# <a name="registering-single-file-generators"></a>Rejestrowanie generatorów jednoplikowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby udostępnić niestandardowego narzędzia w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], musisz się zarejestrować go tak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tworzenia jego instancji i kojarzy ją z określonego typu projektu.  
  
### <a name="to-register-a-custom-tool"></a>Aby zarejestrować narzędzie niestandardowe  
  
1.  Zarejestruj to narzędzie niestandardowe biblioteki DLL w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rejestru lokalnego lub w kluczu HKEY_CLASSES_ROOT rejestru systemu.  
  
     Na przykład poniżej przedstawiono informacje o rejestracji dla zarządzanych MSDataSetGenerator narzędzie niestandardowe, który jest dostarczany z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Utwórz klucz rejestru w żądany [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gałęzi w obszarze generatorów\\*GUID* gdzie *GUID* jest identyfikator GUID jest definiowany przez system projektu określonego języka lub usługi. Nazwa klucza staje się nazwą programową Twojego niestandardowego narzędzia. Klucz niestandardowe narzędzie ma następujące wartości:  
  
    -   (Domyślnie)  
  
         Opcjonalna. Zawiera przyjazny dla użytkownika opis niestandardowego narzędzia. Ten parametr jest opcjonalny, ale zalecane.  
  
    -   CLSID  
  
         Wymagana. Określa identyfikator biblioteki klas składnika modelu COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Wymagana. Wskazuje, czy typy plikom, które są generowane przez niestandardowe narzędzie były dostępne dla projektantów wizualnych. Wartość tego parametru musi być 0 (zero) typy nie są dostępne do projektantów wizualnych lub 1 (co) dla typów dostępnych projektantów wizualnych.  
  
    > [!NOTE]
    >  Należy zarejestrować niestandardowe narzędzie osobno dla każdego języka, dla którego chcesz narzędzie niestandardowe, które mają być dostępne.  
  
     Na przykład MSDataSetGenerator rejestruje się jeden raz dla każdego języka:  
  
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
 [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)   
 [Określanie Namespace domyślnego projektu](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Udostępnianie typów projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Wprowadzenie do obiektu BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)

