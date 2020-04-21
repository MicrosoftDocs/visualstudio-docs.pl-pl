---
title: Element flagi polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649371"
---
# <a name="command-flag-eelement"></a>Flaga polecenia Węgorz
Modyfikuje jego element nadrzędny.

## <a name="syntax"></a>Składnia

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższej sekcji opisano prawidłowe wartości elementu.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Wartość|Opis|
|-----------|-----------------|
|AllowParams (Zezwalaj naparamowanie)|Wskazuje, że użytkownicy mogą wprowadzać parametry polecenia w oknie **Polecenia** po wpisaniu kanonicznej nazwy polecenia.<br /><br /> Ważne dla:`Button`|
|ZawszeKrówz|Menu jest tworzone, nawet jeśli nie ma grup ani przycisków.<br /><br /> Ważne dla:`Menu`|
|Casesensitive|We wpisach użytkownika rozróżniana jest wielkość liter.<br /><br /> Ważne dla:`Combo`|
|CommandWellOnly (PolecenieWellOnly)|Zastosuj tę flagę, jeśli polecenie nie jest wyświetlane w menu najwyższego poziomu i chcesz udostępnić ją do dodatkowego dostosowywania powłoki, na przykład w celu powiązania jej ze skrótem klawiaturowym. Po zainstalowaniu programu VSPackage można dostosować te polecenia, otwierając okno dialogowe **Opcje,** a następnie edytując położenie polecenia w kategorii **Środowisko klawiatury.** Ta flaga nie ma wpływu na położenie na menu skrótów, paskach narzędzi, kontrolerach menu ani podmenu.<br /><br /> Ważne dla: `Button`,`Combo`|
|Domyślna wartość|Domyślnie polecenie jest wyłączone, jeśli VSPackage, który implementuje `QueryStatus` go nie jest załadowany lub metoda nie została wywołana.<br /><br /> Ważne dla: `Button`,`Combo`|
|Domyślnieokło|Zadokowany domyślnie. To ustawienie nie ma już zastosowania do pasków narzędzi, ponieważ są one zawsze zadokowane.|
|Domyślnieniewidoczne|Domyślnie polecenie jest niewidoczne, jeśli vspackage, który `QueryStatus` implementuje nie jest załadowany lub metoda nie została wywołana.<br /><br /> Zaleca się połączenie tego `DynamicVisibility` z flagą.<br /><br /> Ważne `Button`dla: `Combo`, ,`Menu`|
|DontCache (DontCache)|Środowisko programistyczne nie `QueryStatus` buforuje wyników metody dla tego polecenia.<br /><br /> W przypadku menu informuje kontroler menu, aby nie buforować tekstu jego elementów menu. Użyj tej flagi, gdy menu zawiera elementy dynamiczne lub elementy, które mają tekst dynamiczny.<br /><br /> Ważne dla: `Button`,`Menu`|
|DynamicItemStart (Początek dynamicznego)|Wskazuje początek listy dynamicznej. Dzięki temu środowisko do tworzenia listy przez `QueryStatus` sukcesywnie wywołując metodę na elementach listy, dopóki flaga OLECMDERR_E_UNSUPPORTED jest zwracana. Działa to dobrze w przypadku elementów, takich jak ostatnio używane (MRU) listy i listy okien.<br /><br /> Ważne dla:`Button`|
|Dynamiczna niewidzialność|Widoczność polecenia można zmienić `QueryStatus` za pomocą metody lub kontekstu GUID, który znajduje się w `VisibilityConstraints` sekcji.<br /><br /> Dotyczy poleceń wyświetlanych w menu i na paskach narzędzi okna narzędzi, ale nie na paskach narzędzi najwyższego poziomu, które pojawiają się w oknie głównym. Elementy paska narzędzi najwyższego poziomu można wyłączyć, ale nie są ukryte, gdy flaga OLECMDF_INVISIBLE jest zwracana z `QueryStatus` metody. Polecenia paska narzędzi wyświetlane na paskach narzędzi okna narzędzi mogą być ukryte.<br /><br /> W menu ta flaga wskazuje również, że powinna być automatycznie ukryta, gdy wszystkie jej elementy członkowskie są ukryte. Ta flaga jest zazwyczaj przypisana do podmenu, ponieważ menu najwyższego poziomu mają już to zachowanie.<br /><br /> Ta flaga powinna `DefaultInvisible` być połączona z flagą.<br /><br /> Ważne `Button`dla: `Combo`, ,`Menu`|
|Klawisze Filtra|Zobacz temat Filtrowanie kluczy w obszarze [Element kombi](../extensibility/combo-element.md).<br /><br /> Ważne dla:`Combo`|
|FixMenuController (Kontroler FixMenuController)|Jeśli to polecenie jest umieszczone na kontrolerze menu, polecenie jest zawsze ustawieniem domyślnym; oznacza to, że polecenie jest wybierane za każdym razem, gdy wybrany jest sam przycisk kontrolera menu. Jeśli kontroler menu `TextIsAnchorCommand` ma ustawioną flagę, kontroler menu pobiera również `FixMenuController` jego tekst z polecenia, które ma flagę.<br /><br /> Flaga powinna mieć tylko jedno `FixMenuController` polecenie na kontrolerze menu. Jeśli więcej niż jedno polecenie jest tak zaznaczone, ostatnie polecenie w menu staje się poleceniem domyślnym.<br /><br /> Ważne dla:`Button`|
|Ikona Itext|Pokaż ikonę i tekst w menu i pasku narzędzi.<br /><br /> Ważne `Button`dla: `Combo`, ,`Menu`|
|NoAutoComplete (Nieukończenia)|Funkcja automatycznego uzupełnienia jest wyłączona.<br /><br /> Ważne dla:`Combo`|
|NoButtonCustomize (NiebuttonCustomize)|Nie pozwól użytkownikowi dostosować tego przycisku.<br /><br /> Ważne dla: `Button`,`Combo`|
|NoKeyCustomize (Nienaskładka)|Nie włączaj dostosowywania klawiatury.<br /><br /> Ważne dla: `Button`,`Combo`|
|NoShowOnMenuController|Jeśli to polecenie znajduje się na kontrolerze menu, polecenie nie pojawia się na liście rozwijanej.<br /><br /> Ważne dla:`Button`|
|Lista NotInTB|Nie pojawia się na liście dostępnych pasków narzędzi. Ta jest prawidłowa tylko dla typów menu paska narzędzi.<br /><br /> Ważne dla:`Menu`|
|NoToolbarKrówka|Użytkownik nie może zamknąć paska narzędzi. Ta jest prawidłowa tylko dla typów menu paska narzędzi.<br /><br /> Ważne dla:`Menu`|
|Pict|Pokaż tylko ikonę na pasku narzędzi, ale tylko tekst w menu. Jeśli nie określono żadnej ikony, na pasku narzędzi znajduje się klikalne puste miejsce.<br /><br /> Ważne dla:`Button`|
|PostExec (Poekseca)|Powoduje, że polecenie nie blokuje. Środowisko programistyczne odraża wykonywanie, dopóki nie zostaną zakończone wszystkie zapytania przetwarzania wstępnego.<br /><br /> Ważne dla:`Button`|
|RouteToDocs (RouteToDocs)|Polecenie jest kierowane do aktywnego dokumentu.<br /><br /> Ważne dla:`Button`|
|Rozciągliwienie|Gdy ta flaga jest ustawiona, szerokość staje się minimalną szerokością pola kombi, a jeśli na pasku narzędzi jest miejsce, pole kombi zostanie rozciągnięte, aby wypełnić dostępne miejsce. Dzieje się tak tylko wtedy, gdy pasek narzędzi jest zadokowany poziomo, a tylko jedno pole kombi na pasku narzędzi może używać flagi (flaga jest ignorowana we wszystkich z wyjątkiem pierwszego pola kombi).<br /><br /> Ważne dla:`Combo`|
|Zmiany tekstu|Tekst polecenia lub menu można zmienić w czasie `QueryStatus` wykonywania, zazwyczaj za pomocą metody.<br /><br /> Ważne dla: `Button`,`Menu`|
|TextChangesButton (Zmiany tekstu)|Ważne dla:`Button`|
|TextIsAnchorCommand (Wychwytyw.|W przypadku kontrolera menu tekst menu jest pobierany z polecenia domyślnego (kotwicy). Polecenie zakotwiczenia jest ostatnim wybranym lub zatrzaśniętym poleceniem. Jeśli ta flaga nie jest ustawiona, `MenuText` kontroler menu używa własnego pola. Jednak kliknięcie kontrolera menu nadal włącza ostatnio wybrane polecenie z tego kontrolera.<br /><br /> Zaleca się połączenie tej flagi `TextChanges` z flagą.<br /><br /> Ta flaga dotyczy tylko menu typu MenuController lub MenuControllerLatched.<br /><br /> Ważne dla:`Menu`|
|TextMenuCtrlUseMenu|Użyj `MenuText` pola na kontrolerach menu. Polem domyślnym jest `ButtonText`.<br /><br /> Ważne dla:`Button`|
|TextMenuUseButton (Przycisk Użycia tekstu)|Użyj `ButtonText` pola menu. Polem domyślnym jest, `MenuText` jeśli jest określone.<br /><br /> Ważne dla:`Button`|
|Textonly|Pokaż tylko tekst na pasku narzędzi lub menu, ale nie ma ikony, nawet jeśli ikona jest określona.<br /><br /> Ważne dla:`Button`|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element przycisków](../extensibility/buttons-element.md)|Zawiera grupę dla Button elementów [elementu.](../extensibility/button-element.md)|
|[Element Menu](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje VSPackage.|

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (. Vsct) Pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
