---
title: Debugowanie kontrolki ActiveX powiązania danych | Dokumentacja firmy Microsoft
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
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6945d1ccf72385b4d2fbe76736668e84b804e446
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686755"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debugowanie kontrolki ActiveX powiązanego z danymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli tworzysz formant ActiveX, który zostanie powiązany do kontroli źródła danych można utworzyć aplikację kontenera i debugowanie kontrolki ActiveX przy użyciu tego kontenera.  
  
 Na przykład możesz utworzyć aplikację oparte o okna dialogowe MFC i umieszczenie kontrolki powiązane z danymi i kontroli źródła danych, w oknie dialogowym. Tej aplikacji MFC można użyć do testowania w czasie wykonywania oraz jako kontenera pliku wykonywalnego do debugowania formant ActiveX powiązanych z danymi.  
  
## <a name="using-the-test-container"></a>Za pomocą kontenera testu  
 Kontener, który można łatwo modyfikować do obsługi różnych interfejsów albo kontrolki lub kontener, użyć kontenera testu ActiveX jako plik wykonywalny dla sesji debugowania. W kontenerze testów ActiveX, kliknij przycisk **opcje** z **kontenera** menu, aby włączyć różnych interfejsów. Aby uzyskać więcej informacji, zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Jeśli potrzebujesz wkraczać do kontenera kodu podczas debugowania, użyć wersji do debugowania kontenera lub wersję debugowania kontener testu ActiveX. Aby uzyskać więcej informacji, zobacz [TSTCON próbki: Kontener testu kontrolki ActiveX](https://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Zobacz też  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)   
 [Kontrolki ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
