---
title: 'Porady: Tworzenie raportu porównania Profiler w wierszu polecenia z | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fa855b4674963fdb213cd11e9a29361096bff5d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775085"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Porady: tworzenie raportu porównania profilera z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wygenerować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools raport, który porównuje dane dotyczące wydajności dwóch danych profilowania (. VSP lub. Pliki VSPS). Ten raport prezentuje różnic, największe Regresje wydajności i ulepszeń, które wystąpiły w jednej sesji profilowania do innego. Wartości w raporcie przedstawiają zmian lub zmiany z linią bazową pierwszego pliku, który określisz. Tę deltę jest obliczana przez określenie różnica między stara wartość, czyli wartość punktu odniesienia, a wartość wyniku z analizy nowych. Porównywanie danych profilera może bazować na funkcje w kodzie, moduły w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.  
  
 Aby wyświetlić listę identyfikatorów kategorii porównania i pola, wpisz następujące polecenie w wierszu:  
  
 **VSPerfReport/querydifftables zwraca***VspFileName1* *VspFileName2*  
  
 Aby utworzyć raport porównawczy, należy użyć następującej składni:  
  
 **VSPerfReport/diff** `VspFileName1` *VspFileName2* [**/**`Options`]    
  
 Można dodać opcji z poniższej tabeli, aby **VSPerfReport/diff** wiersza polecenia.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**DiffThreshold:**[*wartość*]|Różnica należy pominąć, jeśli jest poniżej tej wartości procentowej wartości progu. Ponadto nowe dane przy użyciu wartości znajdujących się poniżej tego progu nie będą wyświetlane.|  
|**DiffTable:** *TableName*|Ta tabela służy do porównywania plików. Domyślnie jest używany w tabeli funkcji. Określ identyfikator, który znajduje się w **VSPerfReport/querydifftables zwraca**.|  
|**DiffColumn:** *ColumnName*|Ta kolumna służy do porównywania wartości. Domyślnie kolumna % próbek wyłącznych jest używana. Określ identyfikator, który znajduje się w **VSPerfReport/querydifftables zwraca**.|



