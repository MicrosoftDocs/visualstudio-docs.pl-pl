---
title: Biblioteka formantów (kod zarządzany) sieci Web | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a523d593b4c61a7ca730cc60a6ed22a1be541f9c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807598"
---
# <a name="web-control-library-managed-code"></a>Biblioteka formantów sieci Web (zarządzany kod)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon projektu Biblioteka formantów sieci Web tworzy bibliotekę DLL. Ponieważ biblioteki klas jest biblioteką DLL, nie możesz uruchomić go bezpośrednio. Należy utworzyć [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] strona, która osadza formantu. Aby uzyskać więcej informacji, zobacz [szablon biblioteki kontrolki sieci Web](http://msdn.microsoft.com/en-us/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Aby debugować Biblioteka formantów sieci Web (metoda 1)  
  
1.  Otwórz istniejący projekt Biblioteka formantów sieci Web, lub Utwórz nową.  
  
2.  Utwórz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] strona, która osadza formantu.  
  
3.  W witrynie sieci Web, który jest hostem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kontroler testu, Utwórz podkatalog o nazwie `/Code`.  
  
4.  Skopiuj kod źródłowy dla formantu do `/Code` podkatalogu.  
  
5.  Otwórz kod źródłowy w `/Code` podkatalogu i ustawiania punktów przerwania.  
  
6.  Otwórz okno przeglądarki z adresem URL, który wskazuje na kontroler testów. Punkt przerwania w kontrolce spowoduje osiągnięcie i uruchomić debugowanie.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Aby debugować Biblioteka formantów sieci Web (metoda 2)  
  
1.  Utwórz projekt aplikacji hosta i projektu kontrolki sieci Web, w tym samym rozwiązaniu.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy aplikację hosta i wybierz polecenie **Dodaj odwołanie**.  
  
3.  Dodaj odwołanie do projektu sieci web kontroli.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje internetowe ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)



