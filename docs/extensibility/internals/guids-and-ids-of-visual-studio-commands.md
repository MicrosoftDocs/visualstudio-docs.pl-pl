---
title: Identyfikatory GUID i identyfikatory poleceń programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708253"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identyfikatory GUID i identyfikatory poleceń programu Visual Studio
Wartości identyfikatorów GUID i identyfikatorów poleceń zawartych w zintegrowanym środowisku programistycznym Visual Studio (IDE) są zdefiniowane w plikach vsct instalowanych jako część pakietu SDK programu Visual Studio. Aby uzyskać więcej informacji, zobacz [polecenia, menu i grupy zdefiniowane przez IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Aby uzyskać więcej informacji na temat pracy z obiektami IDE zdefiniowanymi w plikach *vsct,* zobacz [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Znajdowanie definicji polecenia
 Ponieważ visual studio definiuje więcej niż 1000 poleceń, jest niepraktyczne, aby wyświetlić je wszystkie tutaj. Zamiast tego wykonaj następujące kroki, aby zlokalizować definicję polecenia.

### <a name="to-locate-a-command-definition"></a>Aby zlokalizować definicję polecenia

1. W programie Visual Studio otwórz następujące pliki w *<ścieżce\>instalacji programu Visual Studio\\ SDK \VisualStudioIntegration\Common\Inc* folder: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    Większość poleceń programu Visual Studio jest zdefiniowana w *plikach SharedCmdDef.vsct* i *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* definiuje polecenia, które odnoszą się do debugera, a *Venusmenu.vsct* definiuje polecenia, które są specyficzne dla tworzenia sieci Web.

2. Jeśli polecenie jest elementem menu, zwróć uwagę na dokładny tekst elementu menu. Jeśli polecenie jest przyciskiem na pasku narzędzi, zanotuj tekst etykietki narzędzia, który pojawia się po wstrzymaniu.

3. Naciśnij **klawisz Ctrl**+**F,** aby otworzyć okno dialogowe **Znajdowanie.**

4. W polu **Znajdź wpisz** tekst odnotowany w kroku 2.

5. Sprawdź, czy **wszystkie otwarte dokumenty** są wyświetlane w polu **Szukaj w** polu.

6. Kliknij przycisk **Znajdź następny,** aż tekst `<Strings>` zostanie zaznaczony w sekcji [elementu Przycisk](../../extensibility/button-element.md).

    Element, `<Button>` w który pojawia się polecenie, jest definicją polecenia.

   Po znalezieniu definicji polecenia można umieścić kopię polecenia w innym menu lub na pasku narzędzi, tworząc `guid` `id` [element CommandPlacement,](../../extensibility/commandplacement-element.md) który ma takie same wartości jak polecenie. Aby uzyskać więcej informacji, zobacz [Tworzenie grup przycisków wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Specjalne przypadki
 W następujących przypadkach tekst menu lub tekst etykietki narzędzia może nie być dokładnie zgodny z tym, co znajduje się w definicji polecenia.

- Elementy menu, które zawierają podkreślony znak, takie jak polecenie **Drukuj** w menu **Plik,** w którym podkreślono *P.*

     Znaki poprzedzone znakiem ampersand (&) w nazwach elementów menu są wyświetlane jako podkreślone. Jednak pliki *.vsct* są zapisywane w formacie XML, który używa znaku ampersand (&) do wskazywania znaków specjalnych i wymaga, aby znak ampersand, który ma być wyświetlany, musi być zapisany jako * &amp;wzmacniacz;*. W związku z tym w pliku *vsct* polecenie **Drukuj** jest wyświetlane jako * &amp;wzmacniacz; Drukowanie*.

- Polecenia z tekstem dynamicznym, takie jak\> **Zapisz** \<bieżącą nazwę pliku, i dynamicznie generowane elementy menu, takie jak elementy na liście Ostatnie **pliki.**

     Nie ma niezawodnego sposobu wyszukiwania tekstu dynamicznego. Zamiast tego znajdź grupę, która obsługuje żądane polecenie, konsultując [identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)i wyszukaj identyfikatory tej grupy. Jeśli definicja polecenia nie ma grupy jako [elementu nadrzędnego,](../../extensibility/parent-element.md)wyszukaj *sharedcmdplace.vsct* i *ShellCmdPlace.vsct* (lub *VsDbgCmdPlace.vsct* dla poleceń debugera) dla `<CommandPlacement>` elementu, który ustawia element nadrzędny polecenia. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*i *VsDbgCmdPlace.vsct* znajdują się w * \<ścieżce\>instalacji programu Visual Studio\\ SDK \VisualStudioIntegration\Common\Inc* folder.

## <a name="see-also"></a>Zobacz też

- [Pliki tabeli poleceń programu Visual Studio (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
