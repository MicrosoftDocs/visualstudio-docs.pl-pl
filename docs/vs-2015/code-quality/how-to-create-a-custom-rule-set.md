---
title: 'Instrukcje: Tworzenie niestandardowego zestawu reguł | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657446"
---
# <a name="how-to-create-a-custom-rule-set"></a>Porady: tworzenie niestandardowego zestawu reguł
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] i [!INCLUDE[vsPro](../includes/vspro-md.md)] można utworzyć i zmodyfikować *zestaw reguł* niestandardowych w celu spełnienia określonych wymagań projektu skojarzonych z analizą kodu. Aby utworzyć niestandardowy zestaw reguł, należy otworzyć co najmniej jeden standardowy zestaw reguł w edytorze zestawu reguł. Następnie można dodać lub usunąć określone reguły, a także zmienić akcję, która występuje, gdy analiza kodu ustali, że reguła została naruszona.

 Aby utworzyć nowy niestandardowy zestaw reguł, Zapisz go przy użyciu nowej nazwy pliku. Niestandardowy zestaw reguł jest automatycznie przypisywany do projektu.

## <a name="opening-the-rule-set-editor"></a>Otwieranie edytora zestawu reguł

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Aby otworzyć pusty plik zestawu reguł w edytorze zestawu reguł

1. W menu **plik** [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] wskaż polecenie **Nowy** , a następnie kliknij polecenie **plik**.

2. W oknie dialogowym **nowy plik** kliknij pozycję **Ogólne** na liście **zainstalowane szablony** , a następnie wybierz pozycję **zestaw reguł analizy kodu**.

3. Zostanie wyświetlony Edytor zestawu reguł. Nie wybrano żadnych reguł na liście edytorów.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Aby utworzyć regułę niestandardową na podstawie jednego istniejącego zestawu reguł

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**.

2. Na karcie **Właściwości** kliknij pozycję **Analiza kodu**.

3. Z listy rozwijanej **zestaw reguł** wykonaj jedną z następujących czynności:

   - Wybierz zestaw reguł, który chcesz dostosować.

     \- lub-

   - Wybierz **\<Browse... >** , aby określić istniejący zestaw reguł, którego nie ma na liście.

4. Kliknij przycisk **Otwórz** , aby wyświetlić reguły w edytorze zestawu reguł.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Aby utworzyć niestandardowy zestaw reguł na podstawie wielu istniejących zestawów reguł

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**.

2. Na karcie **Właściwości** kliknij pozycję **Analiza kodu**.

3. Wybierz **\<Choose wiele zestawów reguł... >** **uruchamiania tego zestawu reguł**.

4. W oknie dialogowym **Dodawanie lub usuwanie zestawów reguł** wybierz zestawy reguł, dla których chcesz utworzyć nowy zestaw reguł, a następnie kliknij przycisk **OK**.

5. Zapisz nowy zestaw reguł.

     Nazwa nowego zestawu reguł jest wybierana na liście **Uruchom ten zestaw reguł** . Można zmienić nazwę wyświetlaną zestawu reguł w następnym kroku.

6. Obowiązkowe Aby zmienić nazwę wyświetlaną zestawu reguł, w menu **Widok** kliknij polecenie **okno właściwości**. Wpisz nazwę wyświetlaną w polu **Nazwa** .

7. Aby dodać, usunąć lub zmodyfikować określone reguły analizy kodu w nowym zestawie reguł, kliknij przycisk **Otwórz**.

## <a name="modifying-a-rule-set"></a>Modyfikowanie zestawu reguł

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Aby zmodyfikować zestaw reguł w edytorze zestawu reguł

- Aby zmienić nazwę wyświetlaną zestawu reguł, w menu **Widok** kliknij polecenie **okno właściwości**. Wprowadź nazwę wyświetlaną w polu **Nazwa** . Zauważ, że nazwa wyświetlana może się różnić od nazwy pliku.

- Aby dodać wszystkie reguły grupy do niestandardowego zestawu reguł, zaznacz pole wyboru grupy. Aby usunąć wszystkie reguły grupy, usuń zaznaczenie pola wyboru.

- Aby dodać określoną regułę do niestandardowego zestawu reguł, zaznacz pole wyboru reguły. Aby usunąć regułę z zestawu reguł, usuń zaznaczenie pola wyboru.

- Aby zmienić akcję wykonywaną w przypadku naruszenia reguły w analizie kodu, kliknij pole **akcji** dla reguły, a następnie wybierz jedną z następujących wartości:

     **Warn** — generuje ostrzeżenie.

     **Błąd** — generuje błąd.

     **Brak** — wyłącza regułę. Ta akcja jest taka sama jak usuwanie reguły z zestawu reguł.

## <a name="changing-the-rule-set-editor-display"></a>Zmienianie wyświetlania edytora zestawu reguł

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Aby grupować, filtrować lub zmieniać pola w edytorze zestawu reguł przy użyciu paska narzędzi edytora zestawu reguł

- Aby rozwinąć reguły we wszystkich grupach, kliknij przycisk **Rozwiń wszystko**.

- Aby zwinąć reguły we wszystkich grupach, kliknij przycisk **Zwiń wszystko**.

- Aby zmienić pole, według którego reguły są grupowane, wybierz pole z listy **Grupuj według** . Aby wyświetlić reguły niezgrupowane, wybierz pozycję **\<None >** .

- Aby dodać lub usunąć pola w kolumnach reguł, kliknij przycisk **Opcje kolumn**.

- Aby ukryć reguły, które nie mają zastosowania do bieżącego rozwiązania, **Ukryj reguły, które nie mają zastosowania do bieżącego rozwiązania**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, które są przypisane do akcji błędu, kliknij przycisk **Pokaż reguły, które mogą generować błędy analizy kodu**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, które są przypisane do akcji ostrzeżenia, kliknij przycisk **Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, do których przypisano akcję **Brak** , kliknij przycisk **Pokaż reguły, które nie są włączone**.

- Aby dodać lub usunąć zestawy reguł domyślnych firmy Microsoft do bieżącego zestawu reguł, kliknij przycisk **Dodaj lub usuń podrzędne zestawy reguł**.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Konfigurowanie analizy kodu dla odwołania do](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [zestawu reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md) projektu zarządzanego
