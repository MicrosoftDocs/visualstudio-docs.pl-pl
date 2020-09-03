---
title: Narzędzia niestandardowe | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708958"
---
# <a name="custom-tools"></a>Narzędzia niestandardowe
*Narzędzia niestandardowe* umożliwiają skojarzenie narzędzia z elementem w projekcie i uruchamianie tego narzędzia za każdym razem, gdy plik zostanie zapisany. Niektóre niestandardowe narzędzia, nazywane czasami *generatorami pojedynczych plików*, są często używane do implementowania tłumaczeń generujących kod na podstawie danych i na odwrót. Na przykład generatory pojedynczych plików tworzą [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] kodu źródłowego z plików *. Settings* i *. resx* . Wygenerowany kod źródłowy zapewnia dostęp z jednoznacznie określonym dostępem do danych w plikach *. Settings* i *. resx* . [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Typy projektów i obsługują niestandardowe narzędzia; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] typy projektów nie są. Własne typy projektów również mogą obsługiwać niestandardowe narzędzia.

 Narzędzia niestandardowe są zarejestrowanymi składnikami, które implementują `IVsSingleFileGenerator` interfejs.

 Narzędzia niestandardowe są skojarzone z `ProjectItem` obiektem interfejsu i są podobne do projektantów i edytorów. Narzędzie niestandardowe pobiera plik reprezentowany przez `ProjectItem` dane wejściowe i zapisuje nowy plik, którego nazwa pliku jest dostarczana przez `DefaultExtension` metodę.

## <a name="in-this-section"></a>W tej sekcji
- [Implementowanie generatorów pojedynczego pliku](../../extensibility/internals/implementing-single-file-generators.md)

 Opisuje sposób korzystania z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu w celu zaimplementowania niestandardowego narzędzia.

- [Rejestrowanie generatorów pojedynczych plików](../../extensibility/internals/registering-single-file-generators.md)

 Zawiera opisy wszystkich wpisów rejestru dla niestandardowego narzędzia.

- [Uwidacznianie typów projektantom wizualizacji](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Wyjaśnia, jak systemy projektów zapewniają obsługę projektantów wizualizacji w celu uzyskiwania dostępu do wygenerowanych klas i typów za pomocą tymczasowych przenośnych plików wykonywalnych (PE).

- [Utrwalanie właściwości elementu projektu](../../extensibility/persisting-the-property-of-a-project-item.md)

 Pokazuje, jak zachować właściwość elementu projektu, na przykład autora pliku źródłowego w pliku projektu.

## <a name="reference"></a>Dokumentacja
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Zawiera szczegółowe informacje na temat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , który przekształca pojedynczy plik wejściowy w jeden plik wyjściowy, który można skompilować lub dodać do projektu.

 <xref:EnvDTE.ProjectItem> Wyjaśnia `ProjectItem` interfejs, który reprezentuje element w projekcie.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Zawiera szczegółowe informacje na temat `DefaultExtension` metody, która pobiera rozszerzenie nazwy pliku, które jest przyznany do nazwy pliku wyjściowego.

## <a name="related-sections"></a>Sekcje pokrewne
- [Rozwiń projekty](../../extensibility/extending-projects.md)

 Opisuje sposób używania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektów i rozwiązań do organizowania plików kodu i plików zasobów oraz sposobu implementacji kontroli źródła.
