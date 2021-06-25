---
title: Command Flag, element | Microsoft Docs
description: Element flagi polecenia modyfikuje jego element nadrzędny. Przejrzyj jego elementy nadrzędne i podrzędne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6356fd02c8045aee9dc48ebc9d30a346159080bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902036"
---
# <a name="command-flag-eelement"></a>Flaga polecenia Eelement
Modyfikuje jego element nadrzędny.

## <a name="syntax"></a>Składnia

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższej sekcji opisano prawidłowe wartości elementów.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Wartość|Opis|
|-----------|-----------------|
|AllowParams|Wskazuje, że użytkownicy mogą wprowadzać parametry polecenia w **oknie** Polecenia podczas wpisywania nazwy kanonicznej polecenia.<br /><br /> Prawidłowe dla: `Button`|
|Zawsze tworzeć|Menu jest tworzone, nawet jeśli nie ma grup ani przycisków.<br /><br /> Prawidłowe dla: `Menu`|
|Casesensitive|W wpisach użytkownika jest wielkość liter.<br /><br /> Prawidłowe dla: `Combo`|
|CommandWellOnly|Zastosuj tę flagę, jeśli polecenie nie jest wyświetlane w menu najwyższego poziomu i chcesz udostępnić ją do dodatkowego dostosowania powłoki, na przykład w celu powiązania jej ze skrótem klawiaturowym. Po zainstalowaniu narzędzia VSPackage można dostosować te polecenia, otwierając **okno** dialogowe Opcje, a następnie edytując umieszczanie poleceń w kategorii **Środowisko klawiatury.** Ta flaga nie ma wpływu na umieszczanie w menu skrótów, paskach narzędzi, kontrolerach menu lub podmenu.<br /><br /> Prawidłowe dla: `Button` , `Combo`|
|DefaultDisabled|Domyślnie polecenie jest wyłączone, jeśli pakiet VSPackage, który go implementuje, nie jest ładowany lub `QueryStatus` metoda nie została wywołana.<br /><br /> Prawidłowe dla: `Button` , `Combo`|
|DefaultDocked|Domyślnie zadokowane. To ustawienie nie dotyczy już pasków narzędzi, ponieważ są one zawsze zadokowane.|
|DefaultInvisible|Domyślnie polecenie jest niewidoczne, jeśli pakiet VSPackage, który go implementuje, nie jest ładowany lub `QueryStatus` metoda nie została wywołana.<br /><br /> Zalecamy połączenie tego z `DynamicVisibility` flagą .<br /><br /> Prawidłowe dla: `Button` , `Combo` , `Menu`|
|DontCache|Środowisko projektowe nie buforuje wyników `QueryStatus` metody dla tego polecenia.<br /><br /> W przypadku menu polecenie informuje kontroler menu, aby nie buforować tekstu elementów menu. Użyj tej flagi, jeśli menu zawiera elementy dynamiczne lub elementy z tekstem dynamicznym.<br /><br /> Prawidłowe dla: `Button` , `Menu`|
|DynamicItemStart|Wskazuje początek listy dynamicznej. Dzięki temu środowisko może tworzyć listę przez kolejne wywoływanie metody w elementach listy, dopóki nie zostanie OLECMDERR_E_UNSUPPORTED `QueryStatus` flaga. Działa to dobrze w przypadku elementów, takich jak listy ostatnio używane (MRU) i listy okien.<br /><br /> Prawidłowe dla: `Button`|
|DynamicVisibility (DynamicVisibility)|Widoczność polecenia można zmienić za pomocą metody lub za pomocą identyfikatora GUID kontekstu, który `QueryStatus` znajduje się w sekcji `VisibilityConstraints` .<br /><br /> Dotyczy poleceń wyświetlanych na paskach narzędzi i menu narzędzi, ale nie na paskach narzędzi najwyższego poziomu, które są wyświetlane w oknie głównym. Elementy paska narzędzi najwyższego poziomu można wyłączyć, ale nie ukryć, gdy OLECMDF_INVISIBLE flaga jest zwracana z `QueryStatus` metody . Polecenia paska narzędzi, które są wyświetlane na paskach narzędzi, mogą być ukryte.<br /><br /> W menu ta flaga wskazuje również, że powinna być automatycznie ukryta, gdy wszystkie jej elementy członkowskie są ukryte. Ta flaga jest zwykle przypisana do podmenu, ponieważ menu najwyższego poziomu już mają takie zachowanie.<br /><br /> Ta flaga powinna być połączona z `DefaultInvisible` flagą .<br /><br /> Prawidłowe dla: `Button` , `Combo` , `Menu`|
|FilterKeys|Zobacz temat Filtering Keys (Klucze filtrowania) w [obszarze Combo, element](../extensibility/combo-element.md).<br /><br /> Prawidłowe dla: `Combo`|
|FixMenuController|Jeśli to polecenie jest umieszczony na kontrolerze menu, polecenie jest zawsze domyślne; oznacza to, że polecenie jest wybierane za każdym razem, gdy wybrany jest przycisk kontrolera menu. Jeśli kontroler menu ma ustawioną flagę, kontroler menu pobiera również tekst z polecenia, `TextIsAnchorCommand` które ma `FixMenuController` flagę .<br /><br /> Tylko jedno polecenie na kontrolerze menu powinno mieć `FixMenuController` flagę . Jeśli więcej niż jedno polecenie jest oznaczone, ostatnie polecenie w menu staje się poleceniem domyślnym.<br /><br /> Prawidłowe dla: `Button`|
|IconAndText|Pokaż ikonę i tekst w menu i na pasku narzędzi.<br /><br /> Prawidłowe dla: `Button` , `Combo` , `Menu`|
|NoAutoComplete|Funkcja automatycznego ukończenia jest wyłączona.<br /><br /> Prawidłowe dla: `Combo`|
|NoButtonCustomize|Nie pozwól użytkownikowi na dostosowanie tego przycisku.<br /><br /> Prawidłowe dla: `Button` , `Combo`|
|NoKeyCustomize|Nie włączaj dostosowywania klawiatury.<br /><br /> Prawidłowe dla: `Button` , `Combo`|
|NoShowOnMenuController|Jeśli to polecenie jest umieszczony na kontrolerze menu, polecenie nie jest wyświetlane na liście rozwijanej.<br /><br /> Prawidłowe dla: `Button`|
|NotInTBList|Nie jest wyświetlana na liście dostępnych pasków narzędzi. Ta opcja jest prawidłowa tylko w przypadku typów menu paska narzędzi.<br /><br /> Prawidłowe dla: `Menu`|
|NoToolbarClose|Użytkownik nie może zamknąć paska narzędzi. Ta opcja jest prawidłowa tylko w przypadku typów menu paska narzędzi.<br /><br /> Prawidłowe dla: `Menu`|
|Pict|Pokaż tylko ikonę na pasku narzędzi, ale tylko tekst w menu. Jeśli nie określono ikony, na pasku narzędzi jest wyświetlana pusta przestrzeń do kliknięcia.<br /><br /> Prawidłowe dla: `Button`|
|PostExec|Sprawia, że polecenie nie blokuje. Środowisko projektowe nie będzie odrażać wykonywania do momentu ukończenia wszystkich zapytań przetwarzania wstępnego.<br /><br /> Prawidłowe dla: `Button`|
|RouteToDocs|Polecenie jest kierowane do aktywnego dokumentu.<br /><br /> Prawidłowe dla: `Button`|
|StretchHorizontally|Gdy ta flaga jest ustawiona, szerokość staje się minimalną szerokością pola kombi, a jeśli na pasku narzędzi jest miejsce, pole kombi rozciąga się w celu wypełnienia dostępnego miejsca. Dzieje się tak tylko wtedy, gdy pasek narzędzi jest zadokowany w poziomie, a tylko jedno pole kombi na pasku narzędzi może używać flagi (flaga jest ignorowana na wszystkich z wyjątkiem pierwszego pola kombi).<br /><br /> Prawidłowe dla: `Combo`|
|TextChanges|Tekst polecenia lub menu można zmienić w czasie działania, zazwyczaj za pomocą `QueryStatus` metody .<br /><br /> Prawidłowe dla: `Button` , `Menu`|
|TextChangesButton|Prawidłowe dla: `Button`|
|TextIsAnchorCommand|W przypadku kontrolera menu tekst menu jest owijony z domyślnego polecenia (kotwicy). Polecenie zakotwiczenia to ostatnie polecenie wybrane lub zatrzaśone. Jeśli ta flaga nie jest ustawiona, kontroler menu używa własnego `MenuText` pola. Jednak kliknięcie kontrolera menu nadal włącza ostatnio wybrane polecenie z tego kontrolera.<br /><br /> Zalecamy połączenie tej flagi z `TextChanges` flagą .<br /><br /> Ta flaga dotyczy tylko menu typu MenuController lub MenuControllerLatched.<br /><br /> Prawidłowe dla: `Menu`|
|TextMenuCtrlUseMenu|Użyj pola `MenuText` na kontrolerach menu. Pole domyślne to `ButtonText` .<br /><br /> Prawidłowe dla: `Button`|
|TextMenuUseButton|Użyj pola `ButtonText` menu. Pole domyślne to `MenuText` , jeśli jest określone.<br /><br /> Prawidłowe dla: `Button`|
|Textonly|Pokazywanie tylko tekstu na pasku narzędzi lub w menu, ale bez ikony, nawet jeśli ikona jest określona.<br /><br /> Prawidłowe dla: `Button`|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Buttons, element](../extensibility/buttons-element.md)|Udostępnia grupę elementów [elementu](../extensibility/button-element.md) Przycisk.|
|[Menus, element](../extensibility/menus-element.md)|Definiuje wszystkie menu implementowanych przez pakiet VSPackage.|

## <a name="see-also"></a>Zobacz też
- [Visual Studio tabeli poleceń (. Vsct) Pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
