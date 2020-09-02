---
title: Biblioteka kontrolek sieci Web (kod zarządzany) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 031f894eb2e117a213f4f9fbbf08ac57a1512d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688173"
---
# <a name="web-control-library-managed-code"></a>Biblioteka formantów sieci Web (zarządzany kod)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon projektu biblioteki kontrolek sieci Web tworzy plik DLL. Ponieważ biblioteka klas jest biblioteką DLL, nie można jej uruchomić bezpośrednio. Należy utworzyć [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stronę, która osadza formant. Aby uzyskać więcej informacji, zobacz [szablon Biblioteka kontrolek sieci Web](https://msdn.microsoft.com/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Aby debugować bibliotekę kontrolek sieci Web (Metoda 1)  
  
1. Otwórz istniejący projekt biblioteki kontrolek sieci Web lub Utwórz nowy.  
  
2. Utwórz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stronę, która osadza formant.  
  
3. W witrynie sieci Web, w której znajduje się [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] zespół programu testowego, Utwórz podkatalog o nazwie `/Code` .  
  
4. Skopiuj kod źródłowy formantu do `/Code` podkatalogu.  
  
5. Otwórz kod źródłowy w `/Code` podkatalogu i ustaw punkty przerwania.  
  
6. Otwórz okno przeglądarki z adresem URL wskazującym zespół testów. Punkt przerwania w kontrolce zostanie trafiony i możesz rozpocząć debugowanie.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Aby debugować bibliotekę kontrolek sieci Web (Metoda 2)  
  
1. Utwórz projekt aplikacji hosta i projekt kontrolki sieci Web w tym samym rozwiązaniu.  
  
2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy aplikację hosta i wybierz polecenie **Dodaj odwołanie**.  
  
3. Dodaj odwołanie do projektu kontrolki sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [ASP.NET aplikacje sieci Web](../debugger/debugging-preparation-aspnet-web-applications.md)
