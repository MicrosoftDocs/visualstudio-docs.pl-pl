---
title: Identyfikatory GUID i identyfikatory Visual Studio poleceń | Microsoft Docs
description: Dowiedz się, jak zlokalizować wartości identyfikatorów GUID i ID poleceń zawartych w Visual Studio zintegrowanym środowisku projektowym (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8442e6430ead8f28d2afc7f51d14968b6999fcd9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898282"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identyfikatory GUID i identyfikatory Visual Studio poleceń
Wartości identyfikatorów GUID i ID poleceń zawartych w zintegrowanym środowisku projektowym (IDE) programu Visual Studio są zdefiniowane w plikach vsct, które są instalowane w ramach zestawu VISUAL STUDIO SDK. Aby uzyskać więcej informacji, zobacz [Polecenia, menu i](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)grupy zdefiniowane w idee .

 Aby uzyskać więcej informacji na temat pracy z obiektami IDE zdefiniowanymi w *plikach vsct,* zobacz [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Znajdowanie definicji polecenia
 Ponieważ Visual Studio więcej niż 1000 poleceń, niepraktyczne jest, aby wyświetlić je wszystkie w tym miejscu. Zamiast tego wykonaj następujące kroki, aby zlokalizować definicję polecenia.

### <a name="to-locate-a-command-definition"></a>Aby zlokalizować definicję polecenia

1. W programie Visual Studio otwórz następujące pliki w folderze *\> \\ \VisualStudioIntegration\Common\Inc* w ścieżce instalacji zestawu<VISUAL STUDIO SDK: *SharedCmdDef.vsct,* *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct,* *Venusmenu.vsct*.

    Większość Visual Studio polecenia są zdefiniowane w *sharedCmdDef.vsct* i *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* definiuje polecenia odnoszące się do debugera, a *Venusmenu.vsct* definiuje polecenia specyficzne dla tworzenia aplikacji internetowych.

2. Jeśli polecenie jest elementem menu, zanotuj dokładny tekst elementu menu. Jeśli polecenie jest przyciskiem na pasku narzędzi, zanotuj tekst etykietki narzędzia, który jest wyświetlany po wstrzymaniu.

3. Naciśnij **klawisz Ctrl** + **F,** aby otworzyć **okno** dialogowe Znajdowanie.

4. W **polu Znajdź** co wpisz tekst zanotowyny w kroku 2.

5. Sprawdź, **czy wszystkie otwarte dokumenty** są wyświetlane w polu **Szukaj** w.

6. Klikaj **przycisk Znajdź** dalej, dopóki tekst nie zostanie wybrany w sekcji elementu `<Strings>` [Button](../../extensibility/button-element.md).

    `<Button>`Elementem, w który pojawia się polecenie, jest definicja polecenia.

   Po odnalezioniu definicji polecenia można umieścić kopię polecenia w innym menu lub pasku narzędzi, tworząc element [CommandPlacement,](../../extensibility/commandplacement-element.md) który ma te same wartości i co `guid` `id` polecenie. Aby uzyskać więcej informacji, zobacz Create reusable groups of buttons (Tworzenie [grup przycisków wielokrotnego użytku).](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>Specjalne przypadki
 W poniższych przypadkach tekst menu lub tekst etykietki narzędzia mogą nie być dokładnie zgodne z definicją polecenia.

- Elementy menu, które zawierają podkreślony znak, takie jak **Drukuj** polecenie **w** menu Plik, w *którym P* jest podkreślony.

     Znaki poprzedzone znakiem handlowego "i" (&) w nazwach elementów menu są wyświetlane jako podkreślone. Jednak *pliki .vsct* są zapisywane w języku XML, który używa znaku ampersand (&) do wskazania znaków specjalnych i wymaga, aby znak ampersand był wyświetlany jako *&amp; i*. W związku z tym w *pliku vsct* polecenie **Print** jest wyświetlane jako *&amp; amp; Wydrukuj .*

- Polecenia z tekstem dynamicznym, takie jak **Zapisz** i dynamicznie generowane elementy menu, takie jak elementy na \<Current Filename\> liście Ostatnie **pliki.**

     Nie ma niezawodnego sposobu wyszukiwania tekstu dynamicznego. Zamiast tego znajdź grupę, która hostuje [żądane](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)polecenie, korzystając z identyfikatorów GUID i identyfikatorów menu programu Visual Studio lub identyfikatorów GUID i identyfikatorów pasków narzędzi programu [Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) i wyszukaj identyfikator tej grupy. Jeśli definicja polecenia nie ma grupy [](../../extensibility/parent-element.md)jako elementu nadrzędnego, wyszukaj element *SharedCmdPlace.vsct* i *ShellCmdPlace.vsct* (lub *VsDbgCmdPlace.vsct* dla poleceń debugera) dla elementu, który ustawia element nadrzędny `<CommandPlacement>` polecenia. *Pliki SharedCmdPlace.vsct,* *ShellCmdPlace.vsct* i *VsDbgCmdPlace.vsct* znajdują się w *\<Visual Studio SDK installation path\> folderze \VisualStudioIntegration\Common\Inc. \\*

## <a name="see-also"></a>Zobacz też

- [Visual Studio plików tabeli poleceń (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
