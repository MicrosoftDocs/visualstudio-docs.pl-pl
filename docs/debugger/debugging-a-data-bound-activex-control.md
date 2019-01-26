---
title: Debugowanie kontrolki ActiveX powiązania danych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f457578b3ac3f07a7493e79024bccb349af3702
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916762"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debugowanie kontrolki ActiveX powiązanego z danymi
Jeśli tworzysz formant ActiveX, który zostanie powiązany do kontroli źródła danych można utworzyć aplikację kontenera i debugowanie kontrolki ActiveX przy użyciu tego kontenera.  
  
 Na przykład możesz utworzyć aplikację oparte o okna dialogowe MFC i umieszczenie kontrolki powiązane z danymi i kontroli źródła danych, w oknie dialogowym. Tej aplikacji MFC można użyć do testowania w czasie wykonywania oraz jako kontenera pliku wykonywalnego do debugowania formant ActiveX powiązanych z danymi.  
  
## <a name="using-the-test-container"></a>Za pomocą kontenera testu  
 Kontener, który można łatwo modyfikować do obsługi różnych interfejsów albo kontrolki lub kontener, użyć kontenera testu ActiveX jako plik wykonywalny dla sesji debugowania. W kontenerze testów ActiveX, kliknij przycisk **opcje** z **kontenera** menu, aby włączyć różnych interfejsów. Aby uzyskać więcej informacji, zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](/cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Jeśli potrzebujesz wkraczać do kontenera kodu podczas debugowania, użyć wersji do debugowania kontenera lub wersję debugowania kontener testu ActiveX. Aby uzyskać więcej informacji, zobacz [TSTCON próbki: Kontener testu kontrolki ActiveX](https://msdn.microsoft.com/library/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Zobacz też  
 [COM i debugowanie ActiveX](../debugger/com-and-activex-debugging.md)   
 [Kontrolki ActiveX](/cpp/mfc/activex-controls)