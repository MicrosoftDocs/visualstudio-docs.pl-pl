---
title: Powłoka programu Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60aa48da701857508f9b6fd7fc3d9d0c0603046e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722053"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Powłoka [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest głównym agentem integracji w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Powłoka zawiera niezbędne funkcje umożliwiające pakietów VSPackage udostępniania wspólnych usług. Ponieważ celem architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest przyjęcie podstawowych funkcji w pakietów VSPackage, powłoka jest strukturą, która zapewnia podstawowe funkcje i obsługuje komunikację między składnikami pakietów VSPackage.

## <a name="shell-responsibilities"></a>Obowiązki powłoki
 Powłoka ma następujące kluczowe obowiązki:

- Obsługa (za pomocą interfejsów COM) podstawowe elementy interfejsu użytkownika (UI). Należą do nich domyślne menu i paski narzędzi, ramki okna dokumentu lub okna podrzędne interfejsu Wielodokumentowego (MDI) oraz ramki okna narzędzi i obsługa dokowania.

- Utrzymywanie uruchomionej listy wszystkich aktualnie otwartych dokumentów w uruchomionej tabeli dokumentu (RDT) w celu koordynowania trwałości dokumentów i zagwarantowania, że nie można otworzyć jednego dokumentu w więcej niż jeden sposób lub na niezgodnych sposobach.

- Obsługa routingu poleceń i interfejsu obsługi poleceń `IOleCommandTarget`.

- Ładowanie pakietów VSPackage w odpowiednim czasie. Ładowanie opóźnień pakietu VSPackage jest niezbędne w celu poprawienia wydajności powłoki.

- Zarządzanie określonymi usługami udostępnionymi, takimi jak <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, zapewnia podstawowe funkcje powłoki i <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, które dostarczają podstawowe funkcje okna.

- Zarządzanie plikami rozwiązania (. sln). Rozwiązania zawierają grupy powiązanych projektów, podobnie jak pliki obszaru roboczego (DSW) w programie Visual C++ 6,0.

- Śledzenie wyboru, kontekstu i waluty całej powłoki. Powłoka śledzi następujące typy elementów:

  - Bieżący projekt

  - Bieżący element projektu lub identyfikator elementu bieżącego <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Bieżący wybór okna **Właściwości** lub `SelectionContainer`

  - Identyfikatory kontekstu interfejsu użytkownika lub CmdUIGuids kontrolujące widoczność poleceń, menu i pasków narzędzi

  - Aktualnie aktywne elementy, takie jak aktywne okno, dokument i Menedżer cofania

  - Atrybuty kontekstu użytkownika, które zapewniają dynamiczną pomoc

  Powłoka również koryguje komunikację między zainstalowanymi pakietów VSPackage i bieżącymi usługami. Obsługuje podstawowe funkcje powłoki i udostępnia je wszystkim pakietów VSPackage zintegrowanym w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Podstawowe funkcje obejmują następujące elementy:

- **Informacje o** oknie dialogowym i ekranie powitalnym

- Okna dialogowe **Dodawanie nowego i Dodawanie istniejącego elementu**

- **Widok klasy** okno i **Przeglądarka obiektów**

- **Odwołania** — okno dialogowe

- Okno **konspektu dokumentu**

- **Dynamiczne okno pomocy**

- **Znajdź** i **Zamień**

- Okna dialogowe **Otwieranie projektu** i **otwieranie plików** w menu **Nowy**

- **Opcje** — okno dialogowe w menu **Narzędzia**

- Okno **Właściwości**

- **Eksplorator rozwiązań**

- Okno **Lista zadań**

- **Przybornik**

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)