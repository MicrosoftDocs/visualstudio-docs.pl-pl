---
title: 'Porady: debugowanie kontrolki ActiveX | Dokumentacja firmy Microsoft'
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
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1e43d94807fa28f86193fc7818b77887d797772
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745153"
---
# <a name="how-to-debug-an-activex-control"></a>Porady: debugowanie kontrolki ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UWAGA]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Aby debugować formant ActiveX, należy określić (plik wykonywalny) dla formantu do uruchamiania w kontenerze.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Aby określić kontener dla sesji debugowania  
  
1.  W Eksploratorze rozwiązań wybierz projekt.  
  
2.  Z **widoku** menu, wybierz **stron właściwości**.  
  
3.  W **strony właściwości projektu** po otwarciu okna dialogowego **właściwości konfiguracji** folder, a następnie wybierz **debugowanie**.  
  
4.  W obszarze **debugowanie** kategorii, zlokalizuj **polecenia** właściwości.  
  
5.  Określ ścieżkę dla kontenera. Na przykład C:\Program Files\Internet Explorer\IEXPLORE. PLIK EXE.  
  
6.  Jeśli używasz aktywnego pulpitu programu Internet Explorer można określić jako kontener, wpisz `/new` w **argumenty wiersza polecenia** pole.  
  
7.  Kliknij przycisk **OK**.  
  
     Jeśli nie zostanie określony kontener w **strony właściwości projektu** okno dialogowe, można określić kontenera po rozpoczęciu debugowania. Po wybraniu polecenia wykonywania, aby rozpocząć debugowanie, [plik wykonywalny debugowania sesji okno dialogowe](../debugger/executable-for-debugging-session-dialog-box.md) pojawia się. Określ nazwę ścieżki kontenera, w oknie dialogowym.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Testowanie właściwości i zdarzeń za pomocą kontenera testu](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)   
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)



