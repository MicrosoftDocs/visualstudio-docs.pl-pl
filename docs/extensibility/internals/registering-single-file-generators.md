---
title: Rejestrowanie generatorów jednoplikowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b0c3bf7c8260506eabf56113992c985e1cc8669
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351012"
---
# <a name="registering-single-file-generators"></a>Rejestrowanie generatorów jednoplikowych
Aby udostępnić niestandardowego narzędzia w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], musisz się zarejestrować go tak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tworzenia jego instancji i kojarzy ją z określonego typu projektu.

### <a name="to-register-a-custom-tool"></a>Aby zarejestrować narzędzie niestandardowe

1. Zarejestruj to narzędzie niestandardowe biblioteki DLL w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rejestru lokalnego lub w kluczu HKEY_CLASSES_ROOT rejestru systemu.

    Na przykład poniżej przedstawiono informacje o rejestracji dla zarządzanych MSDataSetGenerator narzędzie niestandardowe, który jest dostarczany z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Utwórz klucz rejestru w żądany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gałęzi w obszarze generatorów\\*GUID* gdzie *GUID* jest identyfikator GUID jest definiowany przez system projektu określonego języka lub usługi. Nazwa klucza staje się nazwą programową Twojego niestandardowego narzędzia. Klucz niestandardowe narzędzie ma następujące wartości:

   - (Domyślnie)

        Opcjonalna. Zawiera przyjazny dla użytkownika opis niestandardowego narzędzia. Ten parametr jest opcjonalny, ale zalecane.

   - CLSID

        Wymagana. Określa identyfikator biblioteki klas składnika modelu COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.

   - GeneratesDesignTimeSource

        Wymagana. Wskazuje, czy typy plikom, które są generowane przez niestandardowe narzędzie były dostępne dla projektantów wizualnych. Wartość tego parametru musi być 0 (zero) typy nie są dostępne do projektantów wizualnych lub 1 (co) dla typów dostępnych projektantów wizualnych.

   > [!NOTE]
   > Należy zarejestrować niestandardowe narzędzie osobno dla każdego języka, dla którego chcesz narzędzie niestandardowe, które mają być dostępne.

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
   ```

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)
- [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Wprowadzenie do obiektu BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)