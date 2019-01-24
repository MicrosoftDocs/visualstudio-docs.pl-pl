---
title: Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 55ce3ac93f280d5b5cd29fdc533035dc32cbaa8c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773895"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] i [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], można tworzyć i modyfikować niestandardowego *zestaw reguł* do potrzeb określonego projektu skojarzony z analizy kodu. Aby utworzyć regułę niestandardową C++ zestaw, projekt języka C/C++ muszą być otwarte w środowisku IDE programu Visual Studio. Można następnie otwórz zestaw standardowych reguł w edytorze zestawu reguł i następnie dodaj lub usuń określone reguły i opcjonalnie Zmień akcję wykonywaną podczas analizy kodu Określa, że reguły zostały naruszone.  
  
 Aby utworzyć nową regułę niestandardową zestawu, zapisz go przy użyciu nowej nazwy pliku. Niestandardowego zestawu reguł jest przypisywany do projektu.  
  
## <a name="opening-the-rule-set-editor"></a>Otwarcie reguły edytorze zestawu  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Aby utworzyć niestandardową regułę z jednego istniejącego zestawu reguł  
  
1. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.  
  
2. Na **właściwości** kartę, wybrać **analizy kodu**.  
  
3. W **zestaw reguł** listy rozwijanej, wykonaj jedną z następujących czynności:  
  
   - Wybierz zestaw reguł, który chcesz dostosować.  
  
     \- lub —  
  
   - Wybierz  **\<Przeglądaj … >** do określenia zestawu istniejącą regułę, która nie jest na liście.  
  
4. Wybierz **Otwórz** reguły są wyświetlane w edytorze zestawu reguł.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Aby zmodyfikować regułę ustawić w edytorze zestawu reguł  
  
-   Aby zmienić nazwę wyświetlaną zestawu reguł na **widoku** menu, wybierz **okno właściwości**. Wprowadź nazwę wyświetlaną w **nazwa** pole. Należy zauważyć, że nazwa wyświetlana może się różnić od nazwy pliku.  
  
-   Aby dodać zasady grupy do niestandardowego zestawu reguł, zaznacz pole wyboru grupy. Aby usunąć wszystkie zasady grupy, wyczyść pole wyboru.  
  
-   Aby dodać daną regułę do niestandardowego zestawu reguł, zaznacz pole wyboru reguły. Aby usunąć regułę z zestawu reguł, wyczyść pole wyboru.  
  
-   Aby zmienić akcję wykonywaną, gdy naruszenia reguły analizy kodu, wybierz **akcji** pola dla tej reguły, a następnie wybierz jedno z następujących wartości:  
  
     **Ostrzegaj** — generuje ostrzeżenie.  
  
     **Błąd** — generuje błąd.  
  
     **Brak** — wyłącza reguły. Ta akcja jest taka sama jak usunięcie reguły z zestawu reguł.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Do grupy, filtrowanie lub zmiany pól w edytorze zestawu reguł za pomocą paska narzędzi edytora zestawu reguł  
  
-   Aby rozszerzyć reguły we wszystkich grupach, wybierz **Rozwiń wszystko**.  
  
-   Aby zwinąć reguł we wszystkich grupach, wybierz opcję **Zwiń wszystkie**.  
  
-   Aby zmienić pola, które reguły są grupowane według, wybierz pole z **Group By** listy. Aby wyświetlić reguły niezgrupowane, wybierz  **\<Brak >**.  
  
-   Aby dodać lub usunąć pola w kolumnach regułę, wybierz opcję **opcje kolumny**.  
  
-   Aby ukryć reguł, które nie mają zastosowanie do bieżącego rozwiązania, wybierz opcję **Ukryj reguł, które nie mają zastosowanie do bieżącego rozwiązania**.  
  
-   Aby przełączać się między pokazywaniu i ukrywaniu reguł, które są przypisane akcji błędu, wybierz opcję **Pokaż reguły, które mogą generować błędy analizy kodu**.  
  
-   Aby przełączać się między pokazywaniu i ukrywaniu reguł, które są przypisane ostrzeżenie akcję, wybierz opcję **Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**.  
  
-   Aby przełączać się między pokazywaniu i ukrywaniu reguł, które są przypisane **Brak** akcji, wybierz **Pokaż reguły, które nie są włączone**.  
  
-   Aby dodać lub usunąć domyślnej reguły ustawia bieżący zestaw reguł firmy Microsoft, wybierz opcję **apletu Dodaj lub usuń podrzędne zestawy reguł**.
