---
title: Debugowanie kontrolki ActiveX powiązania danych | Dokumentacja firmy Microsoft
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
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae8863b8622987c0676646f45b5659945971c464
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "51768862"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debugowanie kontrolki ActiveX powiązanego z danymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli tworzysz formant ActiveX, który zostanie powiązany do kontroli źródła danych można utworzyć aplikację kontenera i debugowanie kontrolki ActiveX przy użyciu tego kontenera.  
  
 Na przykład możesz utworzyć aplikację oparte o okna dialogowe MFC i umieszczenie kontrolki powiązane z danymi i kontroli źródła danych, w oknie dialogowym. Tej aplikacji MFC można użyć do testowania w czasie wykonywania oraz jako kontenera pliku wykonywalnego do debugowania formant ActiveX powiązanych z danymi.  
  
## <a name="using-the-test-container"></a>Za pomocą kontenera testu  
 Kontener, który można łatwo modyfikować do obsługi różnych interfejsów albo kontrolki lub kontener, użyć kontenera testu ActiveX jako plik wykonywalny dla sesji debugowania. W kontenerze testów ActiveX, kliknij przycisk **opcje** z **kontenera** menu, aby włączyć różnych interfejsów. Aby uzyskać więcej informacji, zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Jeśli potrzebujesz wkraczać do kontenera kodu podczas debugowania, użyć wersji do debugowania kontenera lub wersję debugowania kontener testu ActiveX. Aby uzyskać więcej informacji, zobacz [TSTCON próbki: Kontener testu kontrolki ActiveX](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Zobacz też  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)   
 [Kontrolki ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)



