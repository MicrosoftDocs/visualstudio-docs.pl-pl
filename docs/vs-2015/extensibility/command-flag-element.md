---
title: Element flagi polecenia | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184359"
---
# <a name="command-flag-element"></a>Command Flag, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|AllowParams|Wskazuje, że użytkownicy mogą wprowadzać parametry polecenia w oknie **polecenia** podczas wpisywania nazwy kanonicznej polecenia.<br /><br /> Prawidłowy dla: `Button`|  
|AlwaysCreate|Zostanie utworzone menu, nawet jeśli nie ma żadnych grup lub przycisków.<br /><br /> Prawidłowy dla: `Menu`|  
|CaseSensitive|W wpisach użytkownika jest rozróżniana wielkość liter.<br /><br /> Prawidłowy dla: `Combo`|  
|CommandWellOnly|Zastosuj tę flagę, jeśli polecenie nie pojawia się w menu najwyższego poziomu i chcesz udostępnić je do dodatkowego dostosowania powłoki, na przykład w celu powiązania go ze skrótem klawiaturowym. Po zainstalowaniu pakietu VSPackage można dostosować te polecenia, otwierając okno dialogowe **Opcje** , a następnie edytując położenie polecenia w kategorii **środowisko klawiatury** . Ta flaga nie ma wpływu na umieszczanie w menu skrótów, paskach narzędzi, na kontrolerach menu lub podmenu.<br /><br /> Prawidłowy dla: `Button` , `Combo`|  
|DefaultDisabled|Domyślnie polecenie jest wyłączone, jeśli pakietu VSPackage implementujący go nie jest załadowana lub `QueryStatus` Metoda nie została wywołana.<br /><br /> Prawidłowy dla: `Button` , `Combo`|  
|DefaultDocked|Domyślnie zadokowane. To ustawienie nie ma już zastosowania do pasków narzędzi, ponieważ są zawsze zadokowane.|  
|DefaultInvisible|Domyślnie polecenie jest niewidoczne, jeśli pakietu VSPackage implementujący go nie jest załadowana lub `QueryStatus` Metoda nie została wywołana.<br /><br /> Zalecamy połączenie z `DynamicVisibility` flagą.<br /><br /> Prawidłowy dla: `Button` , `Combo` , `Menu`|  
|DontCache|Środowisko programistyczne nie buforuje `QueryStatus` wyników metody dla tego polecenia.<br /><br /> W przypadku menu nakazuje kontrolerowi menu, aby nie buforować tekstu elementów menu. Użyj tej flagi, gdy menu zawiera elementy dynamiczne lub elementy z tekstem dynamicznym.<br /><br /> Prawidłowy dla: `Button` , `Menu`|  
|DynamicItemStart|Wskazuje początek listy dynamicznej. Umożliwia to środowisku Kompilowanie listy przez kolejne wywołanie `QueryStatus` metody dla elementów listy do momentu zwrócenia flagi OLECMDERR_E_UNSUPPORTED. Jest to dobre rozwiązanie w przypadku elementów, takich jak ostatnio używane (MRU) i listy okien.<br /><br /> Prawidłowy dla: `Button`|  
|DynamicVisibility|Widoczność polecenia można zmienić za pomocą `QueryStatus` metody lub identyfikatora GUID kontekstu, który znajduje się w `VisibilityConstraints` sekcji.<br /><br /> Dotyczy poleceń, które pojawiają się w menu i paska narzędzi okna narzędzi, ale nie na paskach narzędzi najwyższego poziomu, które pojawiają się w oknie głównym. Elementy paska narzędzi najwyższego poziomu można wyłączyć, ale nie ukryte, gdy flaga OLECMDF_INVISIBLE jest zwracana z `QueryStatus` metody. Polecenia paska narzędzi, które pojawiają się na paskach narzędzi okna narzędzi, mogą być ukryte.<br /><br /> W menu ta flaga wskazuje również, że powinna być automatycznie ukryta, gdy wszystkie jej elementy członkowskie są ukryte. Ta flaga jest zwykle przypisana do podmenu, ponieważ menu najwyższego poziomu ma już takie zachowanie.<br /><br /> Ta flaga powinna być połączona z `DefaultInvisible` flagą.<br /><br /> Prawidłowy dla: `Button` , `Combo` , `Menu`|  
|Funkcji|Zobacz temat Filtrowanie kluczy w obszarze [elementu kombi](../extensibility/combo-element.md).<br /><br /> Prawidłowy dla: `Combo`|  
|FixMenuController|Jeśli to polecenie jest ustawione na kontrolerze menu, polecenie jest zawsze domyślnie; oznacza to, że polecenie jest wybierane za każdym razem, gdy zostanie wybrany przycisk kontroler menu. Jeśli kontroler menu ma `TextIsAnchorCommand` ustawioną flagę, kontroler menu pobiera również tekst z polecenia, które ma `FixMenuController` flagę.<br /><br /> Tylko jedno polecenie na kontrolerze menu powinno mieć `FixMenuController` flagę. Jeśli więcej niż jedno polecenie jest oznaczone, to ostatnie polecenie w menu będzie domyślnie poleceniem.<br /><br /> Prawidłowy dla: `Button`|  
|IconAndText|Pokaż ikonę i tekst w menu i na pasku narzędzi.<br /><br /> Prawidłowy dla: `Button` , `Combo` , `Menu`|  
|Noautouzupełnianie|Funkcja autouzupełniania jest wyłączona.<br /><br /> Prawidłowy dla: `Combo`|  
|NoButtonCustomize|Nie Zezwalaj użytkownikowi na Dostosowywanie tego przycisku.<br /><br /> Prawidłowy dla: `Button` , `Combo`|  
|NoKeyCustomize|Nie należy włączać dostosowywania klawiatury.<br /><br /> Prawidłowy dla: `Button` , `Combo`|  
|NoShowOnMenuController|Jeśli to polecenie jest umieszczone na kontrolerze menu, polecenie nie pojawia się na liście rozwijanej.<br /><br /> Prawidłowy dla: `Button`|  
|NotInTBList|Nie jest wyświetlany na liście dostępnych pasków narzędzi. Jest to prawidłowe tylko dla typów menu paska narzędzi.<br /><br /> Prawidłowy dla: `Menu`|  
|NoToolbarClose|Użytkownik nie może zamknąć paska narzędzi. Jest to prawidłowe tylko dla typów menu paska narzędzi.<br /><br /> Prawidłowy dla: `Menu`|  
|Optymalizuj|Pokaż tylko ikonę na pasku narzędzi, ale tylko tekst w menu. Jeśli ikona nie zostanie określona, program wyświetli puste miejsce na pasku narzędzi.<br /><br /> Prawidłowy dla: `Button`|  
|PostExec|Sprawia, że polecenie nie blokuje. Środowisko programistyczne powoduje przeprowadzenie operacji do momentu zakończenia wszystkich zapytań poprzedzających przetwarzanie.<br /><br /> Prawidłowy dla: `Button`|  
|RouteToDocs|Polecenie jest kierowane do aktywnego dokumentu.<br /><br /> Prawidłowy dla: `Button`|  
|StretchHorizontally|Gdy ta flaga jest ustawiona, szerokość zmieni się na minimalną szerokość pola kombi, a jeśli na pasku narzędzi znajduje się pokój, pole kombi rozciąga się w celu wypełnienia dostępnego miejsca. Dzieje się tak tylko wtedy, gdy pasek narzędzi jest zadokowany w poziomie, a tylko jedno pole kombi na pasku narzędzi może używać flagi (flaga jest ignorowana na wszystkich z wyjątkiem pierwszego pola kombi).<br /><br /> Prawidłowy dla: `Combo`|  
|TextMenuUseButton|Użyj `ButtonText` pola dla menu. Pole domyślne to `MenuText` Jeśli jest określone.<br /><br /> Prawidłowy dla: `Button`|  
|TextChanges|Tekst polecenia lub menu można zmienić w czasie wykonywania, zwykle za pomocą `QueryStatus` metody.<br /><br /> Prawidłowy dla: `Button` , `Menu`|  
|TextChangesButton|Prawidłowy dla: `Button`|  
|TextIsAnchorCommand|W przypadku kontrolera menu tekst menu jest pobierany z domyślnego (kotwicy) polecenia. Polecenie kotwicy to ostatnie polecenie wybrane lub zatrzaskowe. Jeśli ta flaga nie jest ustawiona, kontroler menu używa własnego `MenuText` pola. Jednak kliknięcie kontrolera menu nadal włącza ostatnie wybrane polecenie z tego kontrolera.<br /><br /> Zalecamy połączenie tej flagi z `TextChanges` flagą.<br /><br /> Ta flaga ma zastosowanie tylko do menu typu MenuController lub MenuControllerLatched.<br /><br /> Prawidłowy dla: `Menu`|  
|TextMenuCtrlUseMenu|Użyj `MenuText` pola na kontrolerach menu. Pole domyślne to `ButtonText` .<br /><br /> Prawidłowy dla: `Button`|  
|TextMenuUseButton|Użyj `ButtonText` pola dla menu. Pole domyślne to `MenuText` Jeśli jest określone.<br /><br /> Prawidłowy dla: `Button`|  
|TextOnly|Pokaż tylko tekst na pasku narzędzi lub w menu, ale bez ikony, nawet jeśli określono ikonę.<br /><br /> Prawidłowy dla: `Button`|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Buttons, element](../extensibility/buttons-element.md)|Udostępnia grupę dla elementów [elementu Button](../extensibility/button-element.md) .|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje pakietu VSPackage.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
