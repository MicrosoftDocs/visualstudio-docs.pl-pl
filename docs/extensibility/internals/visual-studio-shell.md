---
title: Powłoka programu Visual Studio | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704004"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Powłoka jest głównym agentem integracji w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Powłoka zawiera niezbędne funkcje umożliwiające pakietów VSPackage udostępniania wspólnych usług. Ponieważ celem architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest przyjęcie podstawowych funkcji w pakietów VSPackage, powłoka jest strukturą, która zapewnia podstawowe funkcje i obsługuje komunikację między składnikami pakietów VSPackage.

## <a name="shell-responsibilities"></a>Obowiązki powłoki
 Powłoka ma następujące kluczowe obowiązki:

- Obsługa (za pomocą interfejsów COM) podstawowe elementy interfejsu użytkownika (UI). Należą do nich domyślne menu i paski narzędzi, ramki okna dokumentu lub okna podrzędne interfejsu Wielodokumentowego (MDI) oraz ramki okna narzędzi i obsługa dokowania.

- Utrzymywanie uruchomionej listy wszystkich aktualnie otwartych dokumentów w uruchomionej tabeli dokumentu (RDT) w celu koordynowania trwałości dokumentów i zagwarantowania, że nie można otworzyć jednego dokumentu w więcej niż jeden sposób lub na niezgodnych sposobach.

- Obsługa routingu poleceń i interfejsu obsługi poleceń `IOleCommandTarget` .

- Ładowanie pakietów VSPackage w odpowiednim czasie. Ładowanie opóźnień pakietu VSPackage jest niezbędne w celu poprawienia wydajności powłoki.

- Zarządzanie określonymi usługami udostępnionymi, takimi jak <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> , zapewniającymi podstawowe funkcje powłoki, i <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , które dostarczają podstawowe funkcje okna.

- Zarządzanie plikami rozwiązania (. sln). Rozwiązania zawierają grupy powiązanych projektów, podobnie jak pliki obszaru roboczego (DSW) w Visual C++ 6,0.

- Śledzenie wyboru, kontekstu i waluty całej powłoki. Powłoka śledzi następujące typy elementów:

  - Bieżący projekt

  - Bieżący element projektu lub identyfikator elementu bieżącego <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Bieżący wybór okna **Właściwości** lub `SelectionContainer`

  - Identyfikatory kontekstu interfejsu użytkownika lub CmdUIGuids kontrolujące widoczność poleceń, menu i pasków narzędzi

  - Aktualnie aktywne elementy, takie jak aktywne okno, dokument i Menedżer cofania

  - Atrybuty kontekstu użytkownika, które zapewniają dynamiczną pomoc

  Powłoka również koryguje komunikację między zainstalowanymi pakietów VSPackage i bieżącymi usługami. Obsługuje ona podstawowe funkcje powłoki i udostępnia je wszystkim pakietów VSPackage zintegrowanym w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Podstawowe funkcje obejmują następujące elementy:

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

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
