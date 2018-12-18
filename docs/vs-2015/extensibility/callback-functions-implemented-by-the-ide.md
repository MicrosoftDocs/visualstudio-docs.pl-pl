---
title: Funkcje wywołania zwrotnego implementowane przez środowisko IDE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d2bf114a22419e5ed4621db52a68d266e2e7d0e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807548"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkcje wywołania zwrotnego implementowane przez środowisko IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby Integracja z usługą zintegrowanego środowiska programistycznego (IDE) jako Bezproblemowa, jak to możliwe i w celu zapewnienia ujednoliconego końcowego wtyczka do kontroli źródła można użyć funkcji wywołania zwrotnego, które są implementowane przez środowisko IDE. Wtyczka może wywołać te funkcje w odpowiednim czasie podczas operacji kontroli źródła do przekazywania informacji do IDE; IDE może następnie wyświetlić te informacje jako elementy osadzone w ich natywnym interfejsem użytkownika. Użytkownik ma zmniejszenie fragmentacji środowisko, w tym scenariuszu niż Jeśli wtyczka zatrudnionych własnego interfejsu użytkownika.  
  
 Plik nagłówka wymagane jest scc.h. Domyślna lokalizacja to \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Jest również folder VSIP, który ma przykładowa wtyczka kontroli źródła w \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccOpenProject](../extensibility/sccopenproject-function.md) umożliwiające wyświetlanie komunikatów z kontroli źródła wtyczek za pośrednictwem środowiska IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) gdy IDE nie ma pełny dostęp do informacji, która jest dostępna tylko dla wtyczka do kontroli źródła, takich jak kompletna lista plików w systemie kontroli wersji.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccQueryChanges](../extensibility/sccquerychanges-function.md) operacji.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Zawiera opis funkcji wywołania zwrotnego, który jest używany przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operacji.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 W tym artykule opisano ustawiony przez wywołanie do funkcji wywołania zwrotnego [SccSetOption](../extensibility/sccsetoption-function.md) umożliwiającej wtyczka do kontroli źródła do komunikowania się zmiany nazwy z powrotem do środowiska IDE.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Zostanie otwarty projekt.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Sprawdza, czy lista plików dla ich bieżący stan. Ponadto używa `pfnPopulate` funkcję, aby powiadomić obiekt wywołujący, gdy plik jest niezgodny z kryteriami, które dla `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Sprawdza, czy lista katalogów i plików w projekcie, lub projekty, które są pod kontrolą źródła. Każdy katalog oraz nazwę pliku znaleziono jest przekazywany do funkcji wywołania zwrotnego.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Sprawdza, czy zmiany nazwy, które zostały wprowadzone do listy plików. Każda nazwa pliku jest przekazywany do funkcji wywołania zwrotnego, razem ze statusem zmiany.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Ustawia szeroką gamę opcji. Każda opcja zaczyna się od `SCC_OPT_xxx` i ma swój własny zestaw zdefiniowanych wartości.  
  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)  
 W tym artykule opisano zawartość sekcji odwołanie do zestawu SDK wtyczki kontroli źródła.

