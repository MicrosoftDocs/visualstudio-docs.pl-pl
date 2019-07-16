---
title: Widok interakcji warstwy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd60c855bacaf62beec47c9f977d0ab220ce7ca6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145524"
---
# <a name="tier-interactions-view"></a>Widok interakcji warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje o czasy wykonania w funkcjach aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem [!INCLUDE[vstecado](../includes/vstecado-md.md)]. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]  
  
  Widok interakcji wyświetla dane interakcji między warstwami na dwa okienka:  
  
- W okienku głównym jest drzewa hierarchicznego. Wiersz najwyższego poziomu zawiera zagregowane dane dotyczące połączeń bazy danych [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] strony lub procesu. Węzły podrzędne zawierają zagregowane dane dotyczące połączenia bazy danych elementu nadrzędnego.  
  
- Po kliknięciu węzła wywołania bazy danych w okienku głównym, dane wystąpienia wywołanie bazy danych są wyświetlane w okienku szczegółów.  
  
  Czas jest wyświetlany jako liczbę milisekund lub liczby taktów zegara procesora CPU. Aby zmienić jednostkę czasu, wyświetlany, kliknij przycisk **narzędzia** menu, kliknij przycisk **opcje**, a następnie wybierz jedno z **Pokaż czas wartości w formie** opcje.  
  
## <a name="master-pane"></a>Okienko główne  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|— W przypadku wiersza najwyższego poziomu, nazwa PROFILOWANEGO procesu lub strony sieci Web.<br />– W przypadku wiersza połączenia bazy danych, nazwę serwera, który jest hostem bazy danych.|  
|**Baza danych**|Nazwa bazy danych (tylko wiersze połączenia bazy danych).|  
|**Liczba**|Całkowita liczba żądań, które są generowane przez proces, strony sieci Web lub połączenia z bazą danych.|  
|**Łączny czas, który upłynął**|Całkowity czas spędzony na wykonywaniu każde żądanie jeden z procesów, strony sieci Web lub połączenia z bazą danych.|  
|**Maksymalny czas, który upłynął**|Maksymalny czas poświęcony na wykonanie dowolnego jedno żądanie z procesu, strony sieci Web lub połączenia z bazą danych.|  
|**Minimalny czas trwania**|Minimalny czas spędzony na wykonywaniu każde żądanie jeden z procesów, strony sieci Web lub połączenia z bazą danych.|  
|**Średni czas trwania**|Średni czas spędzony na wykonywaniu żądania z procesu, strony sieci Web lub połączenia z bazą danych.|  
  
## <a name="database-connection-details-pane"></a>W okienku szczegółów połączenia bazy danych  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Tekst polecenia**|Zapytanie SQL żądania.|  
|**Liczba zapytań**|Liczba przypadków, gdy zapytanie zostało uruchomione.|  
|**Łączny czas, który upłynął**|Całkowity czas spędzony na wykonywaniu wystąpień zapytania.|  
|**Maksymalny czas, który upłynął**|Maksymalny czas spędzony na wykonywaniu wszelkie jedno wystąpienie zapytania.|  
|**Minimalny czas trwania**|Minimalny czas spędzony na wykonywaniu wszelkie jedno wystąpienie zapytania.|  
|**Średni czas trwania**|Średni czas spędzony na wykonywaniu wystąpienie zapytania.|
