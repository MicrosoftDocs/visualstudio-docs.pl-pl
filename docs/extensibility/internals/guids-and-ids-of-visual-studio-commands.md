---
title: Identyfikatory GUID i identyfikatory poleceń programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: daf131fd6d7940458252e734ab0cc222f2e3a357
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860973"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identyfikatory GUID i identyfikatory programu Visual Studio poleceń
Identyfikator GUID i identyfikator wartości polecenia zawarte w programie Visual Studio zintegrowane środowisko programistyczne (IDE) są definiowane w .vsct — pliki, które są zainstalowane jako część programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [polecenia definiowane w IDE, menu i grupy](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Aby uzyskać więcej informacji na temat sposobu pracy z obiektami środowiska IDE, które są zdefiniowane w *vsct* plików, zobacz [rozszerzenia menu i poleceń](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Znajdź definicję polecenia
 Ponieważ program Visual Studio definiuje polecenia więcej niż 1000, to niepraktyczne, wymień je wszystkie w tym miejscu. Zamiast tego wykonaj następujące kroki, aby zlokalizować definicji polecenia.

### <a name="to-locate-a-command-definition"></a>Aby zlokalizować definicji poleceń

1. W programie Visual Studio, otwórz następujące pliki w *< ścieżka instalacji programu Visual Studio SDK\>\VisualStudioIntegration\Common\Inc\\*  folderu: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    Większość poleceń programu Visual Studio są zdefiniowane w *SharedCmdDef.vsct* i *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* definiuje polecenia, które odnoszą się do debugera i *Venusmenu.vsct* definiuje polecenia, które są specyficzne dla programowania dla sieci Web.

2. Jeśli polecenie jest element menu, należy pamiętać, dokładny tekst elementu menu. Jeśli polecenie to przycisk na pasku narzędzi, należy pamiętać, tekst etykietki narzędzia, która pojawia się po zatrzymaniu na nim.

3. Naciśnij klawisz **Ctrl**+**F** otworzyć **znaleźć** okno dialogowe.

4. W **Znajdź** wpisz tekst zanotowaną w kroku 2.

5. Upewnij się, że **wszystkimi otwartymi dokumentami** jest wyświetlany w **przeszukania** pole.

6. Kliknij przycisk **Znajdź następny** przycisk, dopóki nie zostanie zaznaczony tekst w `<Strings>` części [Button element](../../extensibility/button-element.md).

    `<Button>` Element, który polecenia pojawia się w jest definicji polecenia.

   Po znalezieniu definicji polecenia Kopiuj polecenia można umieścić w innym menu lub paska narzędzi, tworząc [CommandPlacement, element](../../extensibility/commandplacement-element.md) ma taką samą `guid` i `id` wartości jako polecenie. Aby uzyskać więcej informacji, zobacz [tworzenie wielokrotnego użytku grup przycisków](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Specjalne przypadki
 W następujących przypadkach tekst menu lub tekst etykietki narzędzia może wyglądać inaczej niż w definicji polecenia.

- Elementy menu, które obejmują podkreślony znak, takie jak **drukowania** polecenie **pliku** menu, w którym *P* jest podkreślony.

     Znaki, które są poprzedzone symbolem handlowego "i" (&) znaków w nazwach elementów menu są wyświetlane jako podkreślony. Jednak *vsct* pliki są zapisywane w formacie XML, który używa handlowe "i" (&) znaku, aby wskazać znaki specjalne i wymaga, że musi województw handlowe "i" mają być wyświetlane jako  *&amp;amp;*. Dlatego w *vsct* pliku **drukowania** polecenia jest wyświetlany jako  *&amp;amp; Drukuj*.

- Polecenia, które mają dynamiczne tekstu, takie jak **Zapisz** \<bieżącej, nazwa_pliku\>i dynamicznie wygenerowano elementy menu, takie jak elementy **ostatnio używane pliki** listy.

     Nie ma niezawodne możliwości wyszukiwania na dynamiczny tekst. Zamiast tego należy znaleźć grupy, która obsługuje polecenie żądany przez konsultacji [menu identyfikatory GUID i identyfikatory programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [pasków narzędzi identyfikatory GUID i identyfikatory programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)i wyszukaj identyfikator tej grupy. Jeśli definicji polecenia nie ma grupy jako jego [elementu nadrzędnego](../../extensibility/parent-element.md), wyszukiwanie *SharedCmdPlace.vsct* i *ShellCmdPlace.vsct* (lub  *VsDbgCmdPlace.vsct* dla poleceń debugera) dla `<CommandPlacement>` element, który ustawia element nadrzędny polecenia. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, i *VsDbgCmdPlace.vsct* znajdują się w *\<ścieżka instalacji programu Visual Studio SDK\>\ VisualStudioIntegration\Common\Inc\\* folderu.

## <a name="see-also"></a>Zobacz także
- [MenuCommands programu vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Pliki tabeli (vsct) polecenia programu Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
