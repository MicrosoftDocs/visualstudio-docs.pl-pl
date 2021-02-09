---
title: Debugowanie Data-Bound kontrolki ActiveX | Microsoft Docs
description: Informacje o debugowaniu kontrolki ActiveX powiązanej z kontrolką źródła danych przez utworzenie aplikacji kontenera do debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24de30887185ce4520817904ec6348ef6276b6d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872901"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debugowanie kontrolki ActiveX powiązanego z danymi
Jeśli tworzysz formant ActiveX, który zostanie powiązany z kontrolą źródła danych, możesz utworzyć własną aplikację kontenera i użyć tego kontenera do debugowania kontrolki ActiveX.

 Na przykład możesz utworzyć aplikację MFC opartą na oknach dialogowych i umieścić formant powiązany z danymi oraz formant źródła danych w oknie dialogowym. Ta aplikacja MFC służy do testowania w czasie wykonywania oraz jako plik wykonywalny kontenera do debugowania formantu ActiveX powiązanego z danymi.

## <a name="using-the-test-container"></a>Korzystanie z kontenera testów
 Jeśli chcesz, aby kontener, który można łatwo zmodyfikować, aby obsługiwał różne interfejsy na formancie lub kontenerze, Użyj kontenera testów ActiveX jako pliku wykonywalnego dla sesji debugowania. W kontenerze Test ActiveX kliknij pozycję **Opcje** z menu **kontener** , aby włączyć różne interfejsy. Aby uzyskać więcej informacji, zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testów](/cpp/mfc/testing-properties-and-events-with-test-container).

 Jeśli musisz umieścić w kodzie kontenera podczas debugowania, użyj wersji debugowania kontenera lub użyj wersji debugowania kontenera testów ActiveX. Aby uzyskać więcej informacji, zobacz [przykład TSTCON: kontener testów kontrolki ActiveX](/previous-versions/f9adb5t5(v=vs.100)).

## <a name="see-also"></a>Zobacz też
- [Debugowanie modelu COM i ActiveX](../debugger/com-and-activex-debugging.md)
- [Kontrolki ActiveX](/cpp/mfc/activex-controls)