---
title: Rejestrowanie generatorów pojedynczych plików | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705808"
---
# <a name="registering-single-file-generators"></a>Rejestrowanie generatorów jednoplikowych
Aby udostępnić niestandardowe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]narzędzie w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , należy go zarejestrować, aby można było utworzyć jego wystąpienie i skojarzyć je z określonym typem projektu.

### <a name="to-register-a-custom-tool"></a>Aby zarejestrować narzędzie niestandardowe

1. Zarejestruj bibliotekę DLL narzędzia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] niestandardowego w rejestrze lokalnym lub w rejestrze systemowym, w obszarze HKEY_CLASSES_ROOT.

    Oto na przykład informacje rejestracyjne zarządzanego narzędzia niestandardowego MSDataSetGenerator, które pochodzi z: [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Utwórz klucz rejestru [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w żądanej\\gałęzi w obszarze*GuiD* generatory, gdzie *identyfikator GUID* jest identyfikatorem GUID zdefiniowanym przez system lub usługę projektu określonego języka. Nazwa klucza staje się programową nazwą narzędzia niestandardowego. Niestandardowy klucz narzędzia ma następujące wartości:

   - (Domyślnie)

        Element opcjonalny. Zawiera przyjazny dla użytkownika opis narzędzia niestandardowego. Ten parametr jest opcjonalny, ale zalecane.

   - Clsid

        Wymagany. Określa identyfikator biblioteki klas składnika COM, który <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>implementuje .

   - GeneratesDesignTimeSource

        Wymagany. Wskazuje, czy typy z plików wyprodukowanych przez to narzędzie niestandardowe są udostępniane projektantom wizualnym. Wartość tego parametru musi być (zero) 0 dla typów niedostępnych dla projektantów wizualnych lub (jeden) 1 dla typów dostępnych dla projektantów wizualnych.

   > [!NOTE]
   > Narzędzie niestandardowe należy zarejestrować oddzielnie dla każdego języka, dla którego ma być dostępne narzędzie niestandardowe.

    Na przykład MSDataSetGenerator rejestruje się raz dla każdego języka:

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
