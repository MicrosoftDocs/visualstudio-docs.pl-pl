---
title: Powłoka programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704004"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Powłoka [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest głównym czynnikiem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integracji w . Powłoka zapewnia niezbędne funkcje, aby włączyć VSPackages do udostępniania wspólnych usług. Ponieważ celem architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest vest podstawowej funkcjonalności w VSPackages, powłoki jest strukturą, aby zapewnić podstawowe funkcje i obsługi komunikacji krzyżowej między jego składnik VSPackages.

## <a name="shell-responsibilities"></a>Obowiązki powłoki
 Powłoka ma następujące kluczowe obowiązki:

- Obsługa (za pośrednictwem interfejsów COM) podstawowych elementów interfejsu użytkownika (UI). Należą do nich domyślne menu i paski narzędzi, ramki okien dokumentów lub okna podrzędne interfejsu wielu dokumentów (MDI) oraz ramki okien narzędzi i obsługa dokowania.

- Obsługa listy wszystkich aktualnie otwartych dokumentów w uruchomionej tabeli dokumentów (RDT) w celu skoordynowania trwałości dokumentów i zagwarantowania, że jeden dokument nie może być otwarty w więcej niż jeden sposób lub w sposób niezgodny.

- Obsługa interfejsu routingu i obsługi poleceń, `IOleCommandTarget`.

- Ładowanie vspackages w odpowiednim czasie. Opóźnienie ładowania VSPackage jest konieczne do poprawy wydajności powłoki.

- Zarządzanie niektórymi usługami <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>udostępnionymi, takimi jak <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, który zapewnia podstawowe funkcje powłoki, i , który zapewnia podstawowe funkcje okien.

- Zarządzanie plikami rozwiązania (.sln). Rozwiązania zawierają grupy powiązanych projektów, podobne do plików obszaru roboczego (dsw) w programie Visual C++ 6.0.

- Śledzenie selekcji, kontekstu i waluty w całej skorupie. Powłoka śledzi następujące typy elementów:

  - Bieżący projekt

  - Bieżący element projektu lub ItemID bieżący<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Bieżący wybór okna **Właściwości** lub`SelectionContainer`

  - Identyfikatory kontekstu interfejsu użytkownika lub cmdUIguids, które kontrolują widoczność poleceń, menu i pasków narzędzi

  - Aktualnie aktywne elementy, takie jak aktywne okno, dokument i menedżer cofania

  - Atrybuty Kontekstu użytkownika, które napędzają Pomoc dynamiczną

  Powłoka pośredniczy również komunikacji między zainstalowanymi pakietami VSPackage i bieżącymi usługami. Obsługuje podstawowe cechy powłoki i udostępnia je wszystkim vspackages zintegrowany w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Te podstawowe funkcje obejmują następujące elementy:

- **Informacje o** oknie dialogowym i ekranie powitakiem

- Okna dialogowe **Dodawanie nowego i dodawanie istniejącego elementu**

- Okno **Widok klasy** i **przeglądarka obiektów**

- **Okno** dialogowe Odwołania

- Okno **Konspekt dokumentu**

- Okno **Pomoc dynamiczna**

- **Znajdowanie** i **zamienianie**

- **Otwieranie** okien dialogowych Projekt i **Otwórz plik** w menu **Nowy**

- **Okno** dialogowe Opcje w menu **Narzędzia**

- Okno **Właściwości**

- **Eksplorator rozwiązań**

- Okno **Lista zadań**

- **Przybornik**

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
