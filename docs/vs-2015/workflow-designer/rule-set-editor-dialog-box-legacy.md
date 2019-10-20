---
title: Edytor zestawu reguł — okno dialogowe (starsza wersja) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce9e18a832ceceebc56e294023bc4ae3d06101cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663343"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Edytor zestawu reguł, okno dialogowe (starsza wersja)
W tym temacie opisano sposób użycia okna dialogowego **Edytor zestawu reguł** w starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszej [!INCLUDE[wfd2](../includes/wfd2-md.md)], jeśli chcesz wskazać [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Okno dialogowe **Edytor zestawu reguł** służy do tworzenia i modyfikowania zestawów reguł [zasad zasady](http://go.microsoft.com/fwlink?LinkID=65019) , które są serializowane do pliku reguł.

> [!NOTE]
> Jeśli chcesz otworzyć plik reguł z **edytorem XML z kodowaniem**, musisz zamknąć skojarzone okno projektanta dla przepływu pracy lub działania.

 Aby uzyskać informacje na temat uzyskiwania dostępu do okna dialogowego **Edytor zestawu reguł** , zobacz [How to: Create a Policy Rule Set (starsza wersja)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> Edytor reguł starszej [!INCLUDE[wfd2](../includes/wfd2-md.md)] używany do kierowania [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] nie obsługuje wielodostępności.

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **Edytor zestawu reguł** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Dodaj regułę**|Dodaje nową definicję reguły do zestawu reguł.|
|**Delete**|Usuwa wybraną regułę z zestawu reguł.|
|**Łańcucha**|Określa typ łańcucha do przesyłania dalej do użycia z zestawem reguł. Dostępne opcje to:<br /><br /> -   **pełnego łańcucha**, który określa, że należy używać wszystkich mechanizmów łańcucha do przesyłania dalej: niejawne, przypisywane metody i jawne przy użyciu funkcji **aktualizacji** .<br />-   **sekwencyjne**, które określa, że nie należy używać żadnego łańcucha do przesyłania dalej.<br />-   **tylko jawna aktualizacja**, która określa, że w ramach akcji **aktualizacji** będzie wykonywane tylko łączenie w przód.<br /><br /> Aby uzyskać więcej informacji na temat tworzenia łańcucha do przodu, zobacz [Używanie działania Policy](http://go.microsoft.com/fwlink?LinkID=65004).|
|**Nazwa**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według nazwy.|
|**Priorytet**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według priorytetu.|
|**Ponownej oceny**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł według typu ponownej oceny.|
|**Podgląd reguły**|Nagłówek kolumny listy zestawu reguł. Kliknij, aby posortować listę reguł przez Podgląd warunku i akcji reguły.|
|**Nazwij**|Wprowadź nazwę reguły.|
|**Priorytet**|Wprowadź priorytet dla reguły. Domyślny priorytet wynosi 0.|
|**Ponownej oceny**|Określa typ ponownej oceny reguły, która ma być używana z regułą. Dostępne opcje to:<br /><br /> -   **zawsze**, co powoduje, że reguła zostanie przeszacowana w razie potrzeby.<br />-   **nigdy**, co powoduje, że reguła nigdy nie będzie Szacowana. W takim przypadku reguła jest wykonywana tylko raz.|
|**Wyprzedzeni**|Zaznacz, aby uaktywnić regułę.|
|**Rozgrzewa**|Wprowadź wyrażenie dla warunku reguły. Aby uzyskać informacje na temat składni wyrażeń, zobacz sekcję "wprowadzanie warunku i wyrażeń akcji" na tej stronie.|
|**Następnie akcje:**|Wprowadź wyrażenie dla akcji. Aby uzyskać informacje na temat składni wyrażeń, zobacz sekcję "wprowadzanie warunku i wyrażeń akcji" na tej stronie.|
|**Akcje else:**|Wprowadź wyrażenie dla akcji else. Aby uzyskać informacje na temat składni wyrażeń, zobacz sekcję "wprowadzanie warunku i wyrażeń akcji" na tej stronie.|
|**Ok**|Kliknij, aby zapisać regułę jako plik. rules.|

 Aby uzyskać więcej informacji na temat zestawów reguł, zobacz [Używanie działania Policy](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Wprowadzanie wyrażeń warunku i akcji
 W oknie dialogowym **Edytor zestawu reguł** można wprowadzać wyrażenia dla warunku oraz akcje then i else jako tekst. Możesz to wpisać **.** do edytora, aby odwoływać się do pól, właściwości i metod używanych w przepływie pracy przy użyciu typu menu IntelliSense. Lub można wpisać bezpośrednio nazwę elementu członkowskiego przepływu pracy. Można wywołać metody statyczne dla przywoływanych typów, wpisując nazwę klasy, a po niej nazwę metody.

 Można dodać operatory logiczne do warunku, takie jak i, lub, i nie. Można również dodać predykaty. Predykat jest operatorem binarnym i dwoma operandami. Obsługiwane operatory binarne to = =, >, \<, > = i < =. Obsługiwane argumenty operacji to stała wartość, funkcja arytmetyczna i publiczne elementy członkowskie z zakresem.

 Można określić typ porównania i można ją porównać z **wartością null** lub ciągiem pustym. Można zagnieżdżać wywołania do elementów członkowskich na zmiennej, która zawiera typ złożony, na przykład `this.Address.State == "WA"`.

 Wyrażenia obsługują następujące operatory:

- Operatory relacyjne: = =, =,! =

- Operatory porównania: <, \< =, >, > =

- Operatory arytmetyczne: +,-, *,/, MOD

- Operatory logiczne: i, & &, lub, &#124; &#124;, nie,!

- Operatory bitowe: &,&#124;

  Pierwszeństwo operatorów wyrażeń C# następuje po regułach pierwszeństwa operatorów.

  Aby uzyskać więcej informacji o warunkach, zobacz [Używanie warunków w przepływach pracy](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Funkcje zatrzymania i aktualizacji
 Akcje **:** i **else:** wyrażenia obsługują funkcje **zatrzymania** i **aktualizowania** . Aby użyć funkcji **zatrzymania** , wpisz polecenie **zatrzymania** w **akcji then:** lub **else:** pole tekstowe. Akcja **zatrzymania** powoduje natychmiastowe zatrzymanie wykonywania zestawu reguł, a sterowanie powraca do kodu wywołującego. Funkcja **Update** służy do przesyłania dalej łańcucha.

 Instrukcja **Update** może być wyrażona w edytorze w jednej z dwóch form. w poniższym przykładzie pokazano dwa formularze:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Aby uzyskać więcej informacji o korzystaniu z usługi **Update** w celu tworzenia łańcucha, zobacz [Używanie działania Policy](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Zobacz też
 Okno dialogowe Wybieranie zestawu reguł dla [zasad zabezpieczeń](http://go.microsoft.com/fwlink?LinkID=65019) [(starsza wersja)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [przy użyciu działania zasad](http://go.microsoft.com/fwlink?LinkID=65004) [w przepływach pracy](http://go.microsoft.com/fwlink?LinkID=65009)