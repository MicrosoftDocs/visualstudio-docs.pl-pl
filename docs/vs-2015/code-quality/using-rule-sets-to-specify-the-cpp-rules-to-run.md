---
title: Używanie zestawów reguł do określania reguł języka C++ do uruchomienia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277852"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] i [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] można utworzyć i zmodyfikować *zestaw reguł* niestandardowych w celu spełnienia określonych wymagań projektu skojarzonych z analizą kodu. Aby utworzyć niestandardowy zestaw reguł języka C++, projekt C/C++ musi być otwarty w środowisku IDE programu Visual Studio. Następnie można otworzyć standardowy zestaw reguł w edytorze zestawu reguł, a następnie dodać lub usunąć określone reguły i opcjonalnie zmienić akcję, która występuje, gdy analiza kodu ustali, że reguła została naruszona.  
  
 Aby utworzyć nowy niestandardowy zestaw reguł, Zapisz go przy użyciu nowej nazwy pliku. Niestandardowy zestaw reguł jest automatycznie przypisywany do projektu.  
  
## <a name="opening-the-rule-set-editor"></a>Otwieranie edytora zestawu reguł  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Aby utworzyć regułę niestandardową na podstawie jednego istniejącego zestawu reguł  
  
1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.  
  
2. Na karcie **Właściwości** wybierz pozycję **Analiza kodu**.  
  
3. Z listy rozwijanej **zestaw reguł** wykonaj jedną z następujących czynności:  
  
   - Wybierz zestaw reguł, który chcesz dostosować.  
  
     \- oraz  
  
   - Wybierz **\<Browse...>** , aby określić istniejący zestaw reguł, którego nie ma na liście.  
  
4. Wybierz pozycję **Otwórz** , aby wyświetlić reguły w edytorze zestawu reguł.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Aby zmodyfikować zestaw reguł w edytorze zestawu reguł  
  
- Aby zmienić nazwę wyświetlaną zestawu reguł, w menu **Widok** wybierz polecenie **okno właściwości**. Wprowadź nazwę wyświetlaną w polu **Nazwa** . Zauważ, że nazwa wyświetlana może się różnić od nazwy pliku.  
  
- Aby dodać wszystkie reguły grupy do niestandardowego zestawu reguł, zaznacz pole wyboru grupy. Aby usunąć wszystkie reguły grupy, usuń zaznaczenie pola wyboru.  
  
- Aby dodać określoną regułę do niestandardowego zestawu reguł, zaznacz pole wyboru reguły. Aby usunąć regułę z zestawu reguł, usuń zaznaczenie pola wyboru.  
  
- Aby zmienić akcję wykonywaną w przypadku naruszenia reguły w analizie kodu, wybierz pole **akcji** dla reguły, a następnie wybierz jedną z następujących wartości:  
  
     **Warn** — generuje ostrzeżenie.  
  
     **Błąd** — generuje błąd.  
  
     **Brak** — wyłącza regułę. Ta akcja jest taka sama jak usuwanie reguły z zestawu reguł.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Aby grupować, filtrować lub zmieniać pola w edytorze zestawu reguł przy użyciu paska narzędzi edytora zestawu reguł  
  
- Aby rozwinąć reguły we wszystkich grupach, wybierz **Rozwiń wszystkie**.  
  
- Aby zwinąć reguły we wszystkich grupach, wybierz pozycję **Zwiń wszystko**.  
  
- Aby zmienić pole, według którego reguły są grupowane, wybierz pole z listy **Grupuj według** . Aby wyświetlić reguły niezgrupowane, wybierz opcję **\<None>** .  
  
- Aby dodać lub usunąć pola w kolumnach reguł, wybierz **Opcje kolumn**.  
  
- Aby ukryć reguły, które nie mają zastosowania do bieżącego rozwiązania, wybierz **Ukryj reguły, które nie mają zastosowania do bieżącego rozwiązania**.  
  
- Aby przełączać się między pokazywaniem i ukrywaniem reguł, które są przypisane do akcji błędu, wybierz **Pokaż reguły, które mogą generować błędy analizy kodu**.  
  
- Aby przełączać się między pokazywaniem i ukrywaniem reguł, które są przypisane do akcji ostrzeżenie, wybierz **Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**.  
  
- Aby przełączać się między pokazywaniem i ukrywaniem reguł, do których przypisano akcję **Brak** , wybierz pozycję **Pokaż reguły, które nie są włączone**.  
  
- Aby dodać lub usunąć zestawy reguł domyślnych firmy Microsoft do bieżącego zestawu reguł, wybierz pozycję **Dodaj lub usuń podrzędne zestawy reguł**.
