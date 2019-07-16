---
title: Command Flag, Element | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39b2377dd1599d58eac4ca967ca540d8ce0e6847
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184359"
---
# <a name="command-flag-element"></a>Command Flag, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modyfikuje odpowiedniego elementu nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższej sekcji opisano wartości prawidłowego elementu.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Wartość|Opis|  
|-----------|-----------------|  
|AllowParams|Wskazuje, że użytkownicy mogą wpisać parametry polecenia w **polecenia** okna po wpisaniu nazwy kanonicznej polecenia.<br /><br /> Obowiązuje dla: `Button`|  
|AlwaysCreate|Menu jest tworzony, nawet jeśli go nie ma grup lub przycisków.<br /><br /> Obowiązuje dla: `Menu`|  
|CaseSensitive|Wpisy użytkownika jest rozróżniana wielkość liter.<br /><br /> Obowiązuje dla: `Combo`|  
|CommandWellOnly|Jeśli polecenie nie jest wyświetlany w menu najwyższego poziomu i chcesz udostępnić dostosowywania dodatkowe powłoki, na przykład powiązanie ze skrótem klawiaturowym, należy zastosować tę flagę. Po zainstalowaniu pakietu VSPackage, można dostosować te polecenia, otwierając **opcje** okno dialogowe, a następnie edytując położenie polecenia w obszarze **środowiska klawiatury** kategorii. Ta flaga nie ma wpływu na umieszczanie w menu skrótów, paski narzędzi, kontrolery menu i podmenu.<br /><br /> Prawidłowe dla: `Button`, `Combo`|  
|DefaultDisabled|Domyślnie polecenie jest wyłączona, jeśli nie został załadowany pakietu VSPackage, który implementuje go lub `QueryStatus` nie została wywołana metoda.<br /><br /> Prawidłowe dla: `Button`, `Combo`|  
|DefaultDocked|Zadokowane, domyślnie. To ustawienie nie jest już ma zastosowanie do pasków narzędzi, ponieważ są one zawsze zadokowane.|  
|DefaultInvisible|Domyślnie polecenie jest niewidoczne, jeśli nie został załadowany pakietu VSPackage, który implementuje go lub `QueryStatus` nie została wywołana metoda.<br /><br /> Zaleca się połączyć za pomocą `DynamicVisibility` flagi.<br /><br /> Prawidłowe dla: `Button`, `Combo`, `Menu`|  
|DontCache|Środowisko projektowe nie będzie buforować `QueryStatus` wyników metod dla tego polecenia.<br /><br /> Menu oznacza to kontroler menu, nie będzie buforować tekst jego elementów menu. Należy użyć tej flagi, gdy menu zawiera dynamiczne elementy lub elementy mające dynamiczny tekst.<br /><br /> Prawidłowe dla: `Button`, `Menu`|  
|DynamicItemStart|Wskazuje początek listy dynamicznej. Dzięki temu środowisko w celu utworzenia listy kolejno wywołując `QueryStatus` metoda dla elementów listy, dopóki nie zostanie zwrócony flagi OLECMDERR_E_UNSUPPORTED. Działa to dobrze sprawdza się w elementy takie, jak ostatnio używanych (MRU) listy i listy okna.<br /><br /> Obowiązuje dla: `Button`|  
|DynamicVisibility|Widoczność polecenia można zmienić, modyfikując `QueryStatus` metody lub za pomocą identyfikatora GUID, który znajduje się w kontekście `VisibilityConstraints` sekcji.<br /><br /> Ma zastosowanie do poleceń, które są wyświetlane w menu i na paskach narzędzi okna, ale nie na paski narzędzi najwyższego poziomu, które znajdują się w głównym oknie. Elementy paska narzędzi najwyższego poziomu mogą być wyłączone, ale nie jest to ukryty, gdy flaga OLECMDF_INVISIBLE jest zwracany z `QueryStatus` metody. Mogą być ukrywane polecenia paska narzędzi, które pojawiają się na paskach narzędzi okna.<br /><br /> W menu ta flaga wskazuje także, czy go powinny być automatycznie ukrywane podczas jej elementy członkowskie są ukryte. Ta flaga jest zazwyczaj przypisany do podmenu, ponieważ menu najwyższego poziomu już to zachowanie.<br /><br /> Ta flaga powinna być połączone z `DefaultInvisible` flagi.<br /><br /> Prawidłowe dla: `Button`, `Combo`, `Menu`|  
|KlawiszeFiltru|Zobacz temat filtrowania klucze w ramach [Combo, Element](../extensibility/combo-element.md).<br /><br /> Obowiązuje dla: `Combo`|  
|FixMenuController|Jeśli to polecenie jest ustawiony na kontroler menu, polecenie jest zawsze domyślnie; oznacza to, że polecenie jest zaznaczone, zawsze wtedy, gdy wybrano przycisk menu kontrolera. Jeśli kontroler menu `TextIsAnchorCommand` Flaga, a następnie kontroler menu pobiera również jego tekstu polecenia, który ma `FixMenuController` flagi.<br /><br /> Powinien mieć tylko jedno polecenie na kontrolerze menu `FixMenuController` flagi. Jeśli więcej niż jednego polecenia, dlatego jest oznaczona, ostatnie polecenie w menu staje się domyślnego polecenia.<br /><br /> Obowiązuje dla: `Button`|  
|IconAndText|Pokaż ikonę i tekst w menu i paska narzędzi.<br /><br /> Prawidłowe dla: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Funkcja autouzupełniania jest wyłączona.<br /><br /> Obowiązuje dla: `Combo`|  
|NoButtonCustomize|Zezwala użytkownikowi Dostosowywanie tego przycisku.<br /><br /> Prawidłowe dla: `Button`, `Combo`|  
|NoKeyCustomize|Nie należy włączać Dostosowywanie klawiatury.<br /><br /> Prawidłowe dla: `Button`, `Combo`|  
|NoShowOnMenuController|To polecenie jest ustawiony na kontroler menu, polecenie nie są wyświetlane na liście rozwijanej.<br /><br /> Obowiązuje dla: `Button`|  
|NotInTBList|Nie ma na liście dostępnych pasków narzędzi. Jest to prawidłowe tylko dla typów menu paska narzędzi.<br /><br /> Obowiązuje dla: `Menu`|  
|NoToolbarClose|Użytkownik nie może zamknąć paska narzędzi. Jest to prawidłowe tylko dla typów menu paska narzędzi.<br /><br /> Obowiązuje dla: `Menu`|  
|PICT|Pokaż tylko ikonę na pasku narzędzi, ale tylko tekst menu. Jeśli określono żadnej ikony, pokazuje możesz klikać puste miejsce na pasku narzędzi.<br /><br /> Obowiązuje dla: `Button`|  
|PostExec|Sprawia, że polecenia bez blokowania. Środowisko projektowe odracza wykonywanie do momentu zakończenia wszystkich zapytań przetwarzania wstępnego.<br /><br /> Obowiązuje dla: `Button`|  
|RouteToDocs|Polecenie jest kierowany do aktywnego dokumentu.<br /><br /> Obowiązuje dla: `Button`|  
|StretchHorizontally|Jeśli ta flaga jest ustawiona, szerokość staje się minimalną szerokość pola kombi, a jeśli ma miejsca na pasku narzędzi, pole kombi zostanie rozciągnięty w celu wypełnienia dostępnego miejsca. Dzieje się tak, tylko wtedy, gdy pasek narzędzi w poziomie jest zadokowany tylko jedno pole kombi na pasku narzędzi można użyć flagi (flaga jest ignorowana na wszystkich oprócz pierwszego pola kombi).<br /><br /> Obowiązuje dla: `Combo`|  
|TextMenuUseButton|Użyj `ButtonText` pole menu. To domyślne pole `MenuText` Jeśli została określona.<br /><br /> Obowiązuje dla: `Button`|  
|TextChanges|Tekst polecenia lub menu można zmieniać w czasie wykonywania, zwykle za pomocą `QueryStatus` metody.<br /><br /> Prawidłowe dla: `Button`, `Menu`|  
|TextChangesButton|Obowiązuje dla: `Button`|  
|TextIsAnchorCommand|W przypadku kontrolera menu Tekst menu jest pobierana z polecenie domyślne (zakotwiczenia). Polecenie zakotwiczenia jest ostatnie polecenie wybrane lub zablokowane. Jeśli ta flaga nie jest ustawiona, kontroler menu używa własną `MenuText` pola. Jednak kliknięcie kontroler menu nadal umożliwia ostatniego wybranego polecenia z tego kontrolera.<br /><br /> Zaleca się, czy możesz połączyć tę flagę za pomocą `TextChanges` flagi.<br /><br /> Ta flaga ma zastosowanie tylko do menu typu MenuController lub MenuControllerLatched.<br /><br /> Obowiązuje dla: `Menu`|  
|TextMenuCtrlUseMenu|Użyj `MenuText` pola na kontrolerach menu. To domyślne pole `ButtonText`.<br /><br /> Obowiązuje dla: `Button`|  
|TextMenuUseButton|Użyj `ButtonText` pole menu. To domyślne pole `MenuText` Jeśli została określona.<br /><br /> Obowiązuje dla: `Button`|  
|TextOnly|Wyświetlanie tylko tekstu na pasku narzędzi lub menu, ale brak ikony, nawet jeśli jest określony przez ikonę.<br /><br /> Obowiązuje dla: `Button`|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Buttons, element](../extensibility/buttons-element.md)|Zawiera grupę [Button Element](../extensibility/button-element.md) elementów.|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakietu VSPackage.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
