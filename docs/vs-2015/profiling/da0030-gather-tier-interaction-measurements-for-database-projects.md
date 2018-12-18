---
title: 'DA0030: Zbieraj pomiary interakcji warstw dla projektów bazy danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16d6275074b3cae6b186fe9bb113e32c33e284af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796756"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Gromadzenie pomiarów interakcji warstwowej dla projektów bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0030 |  
| Kategoria | Profilowanie użycia narzędzia |  
| Metoda profilowania | Próbkowanie |  
| Komunikat | Zebranie pomiarów interakcji dla aplikacji wielowarstwowych będzie pomagają zrozumieć wzorców użycia baz danych i danych klucza dostępu opóźnienia. Spróbuj ponownie sprofilować aplikację z włączoną opcją profilowania interakcji między warstwami. |  
| Typ reguły | Informacji |  
  
## <a name="cause"></a>Przyczyna  
 Wywołania <xref:System.Data> metody są znaczna część danych profilowania, a nie zostaną zebrane dane interakcji między warstwami podczas uruchomienia profilowania. Należy wziąć pod uwagę profilowanie ponownie i dodawanie danych o interakcji między warstwami.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła jest uruchamiana zawsze wtedy, gdy istnieje znaczne działanie funkcji, które znajdują się w przestrzeniach nazw System.Data, w tym <xref:System.Data.Linq> <xref:System.Data.Linq>.  
  
 Wielowarstwowe aplikacje za pomocą warstwy usług dla ich warstwy prezentacji i danych. Często Warstwa danych jest oddzielny proces uruchamiany system zarządzania bazami danych, takich jak Microsoft Sql Server. Warstwa danych może być uruchomiony na osobnym komputerze nawet od pozostałej części aplikacji. Profile próbkowania zapewniają mały wgląd w funkcje i usługi uruchomione spoza procesu lub zdalnie.  
  
 Narzędzia profilowania można zbierać informacji chronometrażu dla aplikacji wielowarstwowych, które wchodzą w interakcje z warstwy danych programu Microsoft Sql Server przy użyciu wywołań asynchronicznych do usług ADO.NET. Musisz jawnie włączyć profilowanie interakcji między warstwami. Go nie jest włączona domyślnie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ta reguła jest wyłącznie w celach informacyjnych i może nie wymagać działań korygujących.  
  
 Aby uzyskać informacje dotyczące sposobu dodawania danych o interakcji między warstwami do danych profilowania ze środowiska IDE programu Visual Studio, zobacz [zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md). Aby uzyskać informacje dotyczące sposobu dodawania danych o interakcji między warstwami z wiersza polecenia, zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).



