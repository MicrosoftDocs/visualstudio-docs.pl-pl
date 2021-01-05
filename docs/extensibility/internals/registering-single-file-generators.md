---
title: Rejestrowanie generatorów pojedynczych plików | Microsoft Docs
description: Dowiedz się, jak zarejestrować niestandardowe narzędzie w programie Visual Studio, aby utworzyć jego wystąpienie i skojarzyć je z typem określonego projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a0ce4afeddebdec8519467e1f4249095ce98f6b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875261"
---
# <a name="registering-single-file-generators"></a>Rejestrowanie generatorów jednoplikowych
Aby udostępnić niestandardowe narzędzie w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , należy je zarejestrować, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można było je utworzyć i kojarzyć z określonym typem projektu.

### <a name="to-register-a-custom-tool"></a>Aby zarejestrować narzędzie niestandardowe

1. Zarejestruj bibliotekę DLL narzędzia niestandardowego w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rejestrze lokalnym lub w rejestrze systemowym w obszarze HKEY_CLASSES_ROOT.

    Na przykład poniżej przedstawiono informacje o rejestracji zarządzanego narzędzia niestandardowego MSDataSetGenerator, które zawiera [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Utwórz klucz rejestru w odpowiedniej gałęzi, w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obszarze Identyfikator GUID generatorów \\  , gdzie *GUID* jest identyfikatorem GUID zdefiniowanym przez system lub usługę projektu określonego języka. Nazwa klucza jest programowaną nazwą narzędzia niestandardowego. Klucz niestandardowego narzędzia ma następujące wartości:

   - (Domyślnie)

        Opcjonalny. Zapewnia przyjazny dla użytkownika opis niestandardowego narzędzia. Ten parametr jest opcjonalny, ale zalecany.

   - Identyfikator

        Wymagane. Określa identyfikator biblioteki klas składnika COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .

   - GeneratesDesignTimeSource

        Wymagane. Wskazuje, czy typy z plików utworzonych przez to narzędzie niestandardowe są udostępniane projektantom wizualizacji. Wartość tego parametru musi być równa (zero) 0 dla typów niedostępnych dla projektantów wizualizacji lub (jeden) 1 dla typów dostępnych dla projektantów wizualizacji.

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
   ```

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)
- [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Wprowadzenie do obiektu BuildManager](/previous-versions/8f9kffa8(v=vs.140))