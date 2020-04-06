---
title: Narzędzia niestandardowe | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708958"
---
# <a name="custom-tools"></a>Narzędzia niestandardowe
*Narzędzia niestandardowe* umożliwiają skojarzenie narzędzia z elementem w projekcie i uruchomienie tego narzędzia za każdym razem, gdy plik jest zapisywany. Niektóre narzędzia niestandardowe, czasami określane jako *generatory pojedynczego pliku,* są często używane do implementowania tłumaczy, które generują kod z danych i odwrotnie. Na przykład generatory pojedynczego [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] pliku tworzą i kod źródłowy z plików *.settings* i *.resx.* Wygenerowany kod źródłowy zapewnia silnie typiwany dostęp do danych w plikach *.settings* i *.resx.* [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Typy [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektów obsługują narzędzia niestandardowe; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] typy projektów nie. Własne typy projektów mogą również obsługiwać narzędzia niestandardowe.

 Narzędzia niestandardowe są zarejestrowanymi składnikami, które implementują `IVsSingleFileGenerator` interfejs.

 Narzędzia niestandardowe są `ProjectItem` skojarzone z obiektem interfejsu i są jak projektanci i redaktorzy. Narzędzie niestandardowe pobiera plik reprezentowany przez `ProjectItem` jako dane wejściowe i zapisuje `DefaultExtension` nowy plik, którego nazwa pliku jest dostarczana przez metodę.

## <a name="in-this-section"></a>W tej sekcji
- [Wdrażanie generatorów pojedynczych plików](../../extensibility/internals/implementing-single-file-generators.md)

 W tym artykule opisano, jak zaimplementować narzędzie niestandardowe za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu.

- [Rejestrowanie generatorów pojedynczych plików](../../extensibility/internals/registering-single-file-generators.md)

 Zawiera opisy wszystkich wpisów rejestru dla narzędzia niestandardowego.

- [Udostępnianie typów projektantom wizualnym](../../extensibility/internals/exposing-types-to-visual-designers.md)

 W tym artykule wyjaśniono, w jaki sposób systemy projektów zapewniają obsługę projektantów wizualnych w dostępie do wygenerowanych klas i typów za pośrednictwem tymczasowych przenośnych plików wykonywalnych (PE).

- [Utrwalanie właściwości elementu projektu](../../extensibility/persisting-the-property-of-a-project-item.md)

 Pokazuje, jak utrwalić właściwość elementu projektu, takich jak autor pliku źródłowego, w pliku projektu.

## <a name="reference"></a>Tematy pomocy
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Zawiera szczegółowe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>informacje o programie , który przekształca pojedynczy plik wejściowy w jeden plik wyjściowy, który może być skompilowany lub dodany do projektu.

 <xref:EnvDTE.ProjectItem>W `ProjectItem` tym artykule wyjaśniono interfejs, który reprezentuje element w projekcie.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Zawiera szczegółowe `DefaultExtension` informacje na temat metody, która pobiera rozszerzenie nazwy pliku, który jest podany do nazwy pliku wyjściowego.

## <a name="related-sections"></a>Powiązane sekcje
- [Rozszerzanie projektów](../../extensibility/extending-projects.md)

 W tym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] artykule opisano, jak używać projektów i rozwiązań do organizowania plików kodu i plików zasobów oraz jak zaimplementować kontrolę źródła.
