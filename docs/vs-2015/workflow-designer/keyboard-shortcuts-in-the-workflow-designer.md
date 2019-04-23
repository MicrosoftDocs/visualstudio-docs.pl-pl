---
title: Skróty klawiaturowe w Projektancie przepływu pracy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1a03463d292fa1d4d980c62daa74b291d6a8cb1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117307"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Skróty klawiaturowe w Projektancie przepływu pracy
Wszystkie najważniejsze funkcje [!INCLUDE[wfd1](../includes/wfd1-md.md)] może zostać oceniony przez klawiatury.  
  
## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Nawigowanie w Projektancie przepływu pracy za pomocą klawiatury  
 Wewnątrz [!INCLUDE[vs2010](../includes/vs2010-md.md)], globalne skróty i debugowania skróty dotyczą [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Ponadto wiele [!INCLUDE[wfd2](../includes/wfd2-md.md)] klawiszowych zostały utworzone. W [!INCLUDE[vs2010](../includes/vs2010-md.md)], wszystkie skróty klawiaturowe mogą być ponownie mapowany. Jednak w rehostowanym aplikacji, skróty klawiaturowe są zapisane na stałe.  
  
### <a name="workflow-designer-keyboard-shortcuts"></a>Skróty klawiaturowe w Projektancie przepływu pracy  
 W poniższej tabeli przedstawiono domyślne skróty klawiaturowe, przypisany do [!INCLUDE[wfd2](../includes/wfd2-md.md)] poleceń.  
  
|Skrót|Cel|  
|--------------|-------------|  
|CTRL+E, A|Pokazuje lub ukrywa projektanta argumentów.|  
|CTRL+E, C|Zwija wybrane działanie w miejscu.|  
|CTRL+E, E|Rozwija wybrane działanie w miejscu.|  
|CTRL+E, F|Łączy wybrane działania w elemencie Schemat blokowy.|  
|CTRL+E, I|Pokazuje lub ukrywa projektanta importów.|  
|CTRL+E, M|Przenosi fokus klawiatury do następnego elementu w kolejności tabulacji.|  
|CTRL+E, N|Tworzy nową zmienną zakresu wybranego działania (lub najbardziej).|  
|CTRL+E, O|Pokazuje lub ukrywa mapowanie przeglądów.|  
|CTRL+E, P|Powoduje przejście do elementu nadrzędnego wybranego działania. Przechodzi w górę o jeden poziom w nadrzędnych i zmienia działanie główne na powierzchni projektowej.|  
|CTRL+E, S|Dodaje element z fokusem klawiatury do bieżącego zaznaczenia.|  
|CTRL+E, V|Pokazuje lub ukrywa projektanta zmiennych.|  
|CTRL+E, X|Rozwija wszystkie działania w przepływie pracy.|  
|CTRL+ALT+F6|Przenosi fokus klawiatury z bieżącego obszaru interfejsu użytkownika do obszaru dalej w sekwencji. Kolejność jest następująca:<br /><br /> 1.  Pasek nawigacyjny łączy do stron nadrzędnych.<br />2.  Powierzchnia projektowa<br />3.  Projektanta argumentów/zmienne/importów, jeśli jest otwarty<br />4.  Powłoka|  
  
### <a name="flowchart"></a>Schemat blokowy  
 Na poniższej liście przedstawiono gestów, używaną do utworzenia schematu blokowego klawiatury. Tak jak w pozostałej części [!INCLUDE[wfd2](../includes/wfd2-md.md)], działania są dodawane do powierzchni projektanta za pomocą skrótów globalnego przybornika dołączonym [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
- Aby przenieść działania, wybierz działanie, a następnie używaj klawiszy strzałek Aby zmienić położenie.  
  
- Aby zmienić rozmiar blokowego, Przenieś działanie poza granicą bieżącego schematu blokowego, używając klawiszy ze strzałkami. Schemat blokowy zmieniany jest automatycznie.  
  
- Aby ustawić działanie jako węzeł początkowy, użyj **ustawiony jako Węzeł_początkowy** polecenia w menu kontekstowym.  
  
- Aby połączyć działania:  
  
  1. Wybierz czynność źródła, przechodząc do działania.  
  
  2. Naciśnij klawisze CTRL + E, M tyle razy, zgodnie z potrzebami, aby przenieść fokus klawiatury na działanie docelowe.  
  
  3. Naciśnij klawisze CTRL + E, S, aby dodać działanie docelowe do wyboru.  
  
  4. Naciśnij klawisze CTRL + E, F, aby dodać łącznika ze źródła do miejsca docelowego.  
  
  Uwagi dotyczące łączenia działań przez klawiatury:  
  
- Aby włączyć wiele połączeń w tym samym czasie, dodając więcej działań do wyboru przed naciskając klawisze CTRL + E, F. Połączenia są nawiązywane w kolejności, czy działania zostały dodane do zaznaczenia.  
  
- Jeśli nie można połączyć dwa działania na przykład jeśli działania źródłowego ma już połączenia wychodzącego inne połączenia między działaniami w zaznaczeniu nadal zostały wprowadzone, jeśli to możliwe.  
  
- Gdy **FlowDecision** jest dołączony do zaznaczenia i **FlowDecision** ma Brak wychodzących łączników, łącznik jest umieszczany na **True** gałęzi.  
  
### <a name="expression-editing"></a>Edytowanie wyrażeń  
 Domyślnie, domyślne skróty klawiaturowe dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] edycji tekstu zastosować wewnątrz edytora wyrażeń w [!INCLUDE[wfd2](../includes/wfd2-md.md)], zastosowanie mają poniższe ograniczenia:  
  
- Ponowne mapowanie skróty klawiaturowe dla następujących poleceń nie ma znaczenia. Domyślne skróty klawiaturowe można używać tylko dostępu do tych poleceń podczas edycji wyrażenia.  
  
    1. Wytnij  
  
    2. Kopiuj  
  
    3. Wklej  
  
    4. Zaznacz wszystko  
  
    5. Cofnij  
  
    6. Wykonaj ponownie  
  
- Aby ponownie zamapować skróty klawiaturowe dla wyrażenia polecenia wewnątrz edycji [!INCLUDE[wfd2](../includes/wfd2-md.md)] w [!INCLUDE[vs2010](../includes/vs2010-md.md)], Edytuj skróty w [!INCLUDE[wfd2](../includes/wfd2-md.md)] zakresu. Zmiany wprowadzone w zakresie Edytor tekstu nie automatycznie dotyczą [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Jeśli chcesz ponownie zmapować skróty w obu miejscach, należy najpierw zastosować zmiany dwukrotnie (raz dla każdego zakresu).