---
title: Skróty klawiaturowe w Projektant przepływu pracy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f7bc701c4a7009d402c778356a290ce4e129bb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658974"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Skróty klawiaturowe w Projektancie przepływu pracy
Wszystkie podstawowe funkcje programu są dostępne na [!INCLUDE[wfd1](../includes/wfd1-md.md)] klawiaturze.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Nawigowanie Projektant przepływu pracy przy użyciu klawiatury
 Wewnątrz [!INCLUDE[vs2010](../includes/vs2010-md.md)] , Skróty globalne i skróty debugowania mają zastosowanie do [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Ponadto [!INCLUDE[wfd2](../includes/wfd2-md.md)] zostały utworzone pewne skróty klawiaturowe. W programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] wszystkie skróty klawiaturowe mogą być ponownie mapowane. Jednak w aplikacji przehostowanej te skróty klawiaturowe są stałe.

### <a name="workflow-designer-keyboard-shortcuts"></a>Skróty klawiaturowe Projektant przepływu pracy
 Poniższa tabela podsumowuje domyślne skróty klawiaturowe przypisane do [!INCLUDE[wfd2](../includes/wfd2-md.md)] poleceń.

|Skrót|Przeznaczenie|
|--------------|-------------|
|CTRL + E, A|Pokazuje lub ukrywa projektanta argumentów.|
|CTRL + E, C|Zwija wybrane działanie.|
|CTRL + E, E|Rozwija wybrane działanie na miejscu.|
|CTRL + E, F|Łączy wybrane działania w schemacie blokowym.|
|CTRL + E, I|Pokazuje lub ukrywa projektanta importów.|
|CTRL + E, M|Przesuwa fokus klawiatury do następnego elementu w kolejności tabulacji.|
|CTRL + E, N|Tworzy nową zmienną w zakresie wybranego działania (lub najbliższą).|
|CTRL + E, O|Pokazuje lub ukrywa mapę przeglądu.|
|CTRL + E, P|Powoduje przejście do elementu nadrzędnego wybranego działania. Powoduje to przejście do jednego poziomu w nawigacji nawigacyjnej i zmianę działania głównego na powierzchni projektanta.|
|CTRL + E, S|Dodaje element z fokusem klawiatury do bieżącego zaznaczenia.|
|CTRL + E, V|Pokazuje lub ukrywa projektanta zmiennych.|
|CTRL + E, X|Rozwija wszystkie działania w przepływie pracy.|
|CTRL + ALT + F6|Przenosi fokus klawiatury z bieżącego obszaru interfejsu użytkownika do następnego obszaru w sekwencji. Kolejność jest następująca:<br /><br /> 1. pasek nawigacyjny.<br />2. powierzchnia projektanta<br />3. argumenty/zmienne/Importy projektant w przypadku otwarcia<br />4. Shell|

### <a name="flowchart"></a>Schemat blokowy
 Na poniższej liście przedstawiono gesty używane do konstruowania schematu blokowego za pomocą klawiatury. Podobnie jak w pozostałej części [!INCLUDE[wfd2](../includes/wfd2-md.md)] , działania są dodawane do powierzchni projektanta przy użyciu globalnych skrótów przybornika dostępnych w [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

- Aby przenieść działanie, wybierz działanie i użyj klawiszy strzałek, aby zmienić ich położenie.

- Aby zmienić rozmiar schematu blokowego, Przenieś działanie poza bieżącą krawędź schematu blokowego za pomocą klawiszy strzałek. Automatycznie zmieniany jest rozmiar schematu blokowego.

- Aby ustawić działanie jako węzeł początkowy, użyj polecenia **Set as parametr StartNode** w menu kontekstowym.

- Aby połączyć działania:

  1. Wybierz działanie źródłowe, naciskając klawisz Tab do działania.

  2. Naciśnij klawisze CTRL + E, M tyle razy, ile jest to konieczne, aby przenieść fokus klawiatury do działania docelowego.

  3. Naciśnij klawisze CTRL + E, aby dodać działanie docelowe do zaznaczenia.

  4. Naciśnij klawisze CTRL + E, F, aby dodać łącznik ze źródła do miejsca docelowego.

  Uwagi dotyczące łączenia działań według klawiatury:

- Można utworzyć wiele połączeń w tym samym czasie, dodając więcej działań do zaznaczenia przed naciśnięciem kombinacji klawiszy CTRL + E, F. Połączenia są wykonywane w kolejności, w jakiej działania zostały dodane do zaznaczenia.

- Jeśli para działań nie może być połączona, na przykład jeśli działanie źródłowe ma już połączenie wychodzące, inne połączenia między działaniami w ramach zaznaczenia nadal są wykonywane zawsze, gdy jest to możliwe.

- Gdy **FlowDecision** jest dołączany do zaznaczenia, a **FlowDecision** nie ma łączników wychodzących, łącznik jest umieszczany w gałęzi **prawdy** .

### <a name="expression-editing"></a>Edytowanie wyrażeń
 Domyślnie domyślne skróty klawiaturowe do [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] edycji tekstu mają zastosowanie w edytorze wyrażeń w [!INCLUDE[wfd2](../includes/wfd2-md.md)] , z następującymi ograniczeniami:

- Ponowne mapowanie skrótów klawiaturowych dla następujących poleceń nie ma żadnego wpływu. Możesz użyć domyślnych skrótów klawiaturowych, aby uzyskać dostęp do tych poleceń podczas edytowania wyrażenia.

    1. Wytnij

    2. Kopiuj

    3. Wklej

    4. Zaznacz wszystko

    5. Cofnij

    6. Ponów

- Aby ponownie zamapować skróty klawiaturowe poleceń edycji wyrażeń wewnątrz [!INCLUDE[wfd2](../includes/wfd2-md.md)] w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] , należy edytować skróty w [!INCLUDE[wfd2](../includes/wfd2-md.md)] zakresie. Zmiany wprowadzone w zakresie edytora tekstu nie są automatycznie stosowane do programu [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Jeśli chcesz ponownie mapować skróty w obu miejscach, musisz zastosować zmiany dwukrotnie (raz dla każdego zakresu).