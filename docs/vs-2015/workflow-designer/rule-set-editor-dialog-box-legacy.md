---
title: Zestaw reguł edytora okno dialogowe (starsza wersja) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3827ef20ae5eb67c1052b6c7f6147d736013490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438888"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Edytor zestawu reguł, okno dialogowe (starsza wersja)
W tym temacie opisano sposób użycia **Edytor zestawu reguł** okno dialogowe w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 **Edytor zestawu reguł** okno dialogowe służy do tworzenia i modyfikowania [działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) zestawy, które są serializowane w pliku Rules reguły.  
  
> [!NOTE]
> Jeśli chcesz otworzyć plik Rules z **Edytor XML z kodowaniem**, należy zamknąć skojarzone okno projektanta przepływu pracy lub działania.  
  
 Aby uzyskać informacje o tym, jak uzyskać dostęp do **Edytor zestawu reguł** okno dialogowe, zobacz [jak: Tworzenie zestawu reguł działania PolicyActivity (starsza wersja)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
> W edytorze zasad starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] umożliwiający docelowy: [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] nie obsługuje wielowersyjności kodu w programie.  
  
 W poniższej tabeli opisano elementy interfejsu użytkownika **Edytor zestawu reguł** okno dialogowe.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Dodaj regułę**|Dodaje nową definicję reguły do zestawu reguł.|  
|**Delete**|Usuwa wybraną regułę z zestawu reguł.|  
|**Tworzenie łańcucha**|Określa, jakiego typu do przodu łańcucha za pomocą zestawu reguł. Dostępne opcje to:<br /><br /> -   **Pełne tworzenie łańcucha**, co określa, aby korzystać z wszystkich do przodu mechanizmów łańcucha: niejawne, przypisywanie metody i za pomocą jawnego **aktualizacji** funkcji.<br />-   **Sekwencyjne**, która określa, że nie należy używać do przodu łańcucha.<br />-   **Tylko jawne aktualizacji**, co określa, aby wykonać tylko do przodu łańcucha na **aktualizacji** akcji.<br /><br /> Aby uzyskać więcej informacji na temat łańcucha do przodu, zobacz [przy użyciu działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Nazwa**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według nazwy.|  
|**Priorytet**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według priorytetu.|  
|**Ponownej oceny**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według typu ponownej oceny.|  
|**Reguły (wersja zapoznawcza)**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł w wersji zapoznawczej warunek reguły i akcje.|  
|**Nazwa:**|Wprowadź nazwę reguły.|  
|**Priorytet:**|Wprowadź priorytet reguły. Priorytet domyślny jest 0.|  
|**Ponownej oceny:**|Określa, jakiego typu ponownej oceny reguł, do użycia z regułą. Dostępne opcje to:<br /><br /> -   **Zawsze**, co powoduje, że reguła go obliczyć ponownie zgodnie z potrzebami.<br />-   **Nigdy nie**, co powoduje, że reguła nigdy go obliczyć ponownie. W tym przypadku reguła jest wykonywana tylko raz.|  
|**Aktywne**|Sprawdź, aby uaktywnić reguły.|  
|**Warunek:**|Wprowadź wyrażenie dla warunku reguły. Aby uzyskać informacje dotyczące składni wyrażenia zobacz sekcję "Wprowadzanie warunków i akcji wyrażeń" na tej stronie.|  
|**Następnie akcje:**|Wprowadź wyrażenie następnie akcji. Aby uzyskać informacje dotyczące składni wyrażenia zobacz sekcję "Wprowadzanie warunków i akcji wyrażeń" na tej stronie.|  
|**Inne akcje:**|Wprowadź wyrażenia Else akcji. Aby uzyskać informacje dotyczące składni wyrażenia zobacz sekcję "Wprowadzanie warunków i akcji wyrażeń" na tej stronie.|  
|**OK**|Kliknij, aby zapisać regułę, Ustaw plik rules.|  
  
 Aby uzyskać więcej informacji na temat zestawów reguł, zobacz [przy użyciu działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="entering-condition-and-action-expressions"></a>Wprowadź warunek i wyrażenia akcji  
 Wprowadź wyrażenia dla warunku, a następnie i inne operacje jako tekst w ich odpowiednich tekst pola **Edytor zestawu reguł** okno dialogowe. Możesz wpisać **to.** do edytora, aby odwoływać się do pola, właściwości i metody używane w przepływie pracy przy użyciu typu menu funkcji IntelliSense. Lub możesz bezpośrednio wpisać nazwę elementu członkowskiego przepływu pracy. Możesz wywołać metody statycznej na wskazanych typów kolekcji, wpisując nazwę klasy, a następnie nazwę metody.  
  
 Operatory logiczne można dodać do warunku, takich jak AND, OR i NOT. Można również dodać predykatów. Predykat jest operator binarny i dwóch argumentów operacji. Operatory dwuargumentowe, obsługiwane są ==, >, \<, > =, i < =. Obsługiwane argumenty operacji są wartości stałej, funkcja arytmetyczne i zakresie publiczne elementy członkowskie.  
  
 Można określić typ porównania i możesz porównać **null** ani być pustym ciągiem. Można zagnieździć wywołań do elementów członkowskich w zmiennej, która zawiera typ złożony, na przykład `this.Address.State == "WA"`.  
  
 Wyrażenia obsługują następujące operatory:  
  
- Operatory relacyjne: ==, =,! =  
  
- Operatory porównania: <, \<=, >, > =  
  
- Operatory arytmetyczne: +, -, *, / MOD  
  
- Operatory logiczne: PONADTO &AMP; &AMP;, OR &AMP;#124; &AMP;#124;, NIE!  
  
- Bitwise operators: &, &#124;  
  
  Kolejność wykonywania wyrażenia następuje reguły pierwszeństwa operatorów języka C#.  
  
  Aby uzyskać więcej informacji o warunkach, zobacz [za pomocą warunków w przepływach pracy](http://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).  
  
### <a name="halt-and-update-functions"></a>Zatrzymaj i aktualizacji funkcji  
 **Następnie akcje:** i **inne akcje:** wyrażenia obsługują **zatrzymanie** i **aktualizacji** funkcji. Do użycia **zatrzymanie** funkcji, wpisz **zatrzymanie** do **następnie akcji:** lub **Else akcji:** pola tekstowego. **Zatrzymanie** czynność powoduje wykonanie zestawu reguł zatrzymać natychmiast, a sterowanie powraca do wywołującego kodu. Możesz użyć **aktualizacji** funkcji z łańcucha do przodu.  
  
 **Aktualizacji** poufności informacji mogą być wyrażone w edytorze w jednej z dwóch formach; obie formy są wyświetlane w następującym przykładzie:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Aby uzyskać więcej informacji o korzystaniu z **aktualizacji** wraz z łańcucha do przodu [przy użyciu działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="see-also"></a>Zobacz też  
 [Działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Zestaw wybierz regułę, okno dialogowe (starsza wersja)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Przy użyciu działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Za pomocą warunków w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009)