---
title: 'Instrukcje: Debugowanie kontrolki ActiveX | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c76167468d9eb6fbe93c3bef0c4ae8c15634fc5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894433"
---
# <a name="how-to-debug-an-activex-control"></a>Instrukcje: Debugowanie kontrolki ActiveX

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

Aby debugować formant ActiveX, należy określić (plik wykonywalny) dla formantu do uruchamiania w kontenerze.

## <a name="to-specify-a-container-for-the-debug-session"></a>Aby określić kontener dla sesji debugowania

1. W Eksploratorze rozwiązań wybierz projekt.

2. Z **widoku** menu, wybierz **stron właściwości**.

3. W **strony właściwości projektu** po otwarciu okna dialogowego **właściwości konfiguracji** folder, a następnie wybierz **debugowanie**.

4. W obszarze **debugowanie** kategorii, zlokalizuj **polecenia** właściwości.

5. Określ ścieżkę dla kontenera. Na przykład C:\Program Files\Internet Explorer\IEXPLORE. PLIK EXE.

6. Jeśli używasz aktywnego pulpitu programu Internet Explorer można określić jako kontener, wpisz `/new` w **argumenty wiersza polecenia** pole.

7. Kliknij przycisk **OK**.

     Jeśli nie zostanie określony kontener w **strony właściwości projektu** okno dialogowe, można określić kontenera po rozpoczęciu debugowania. Po wybraniu polecenia wykonywania, aby rozpocząć debugowanie, [plik wykonywalny debugowania sesji okno dialogowe](../debugger/executable-for-debugging-session-dialog-box.md) pojawia się. Określ nazwę ścieżki kontenera, w oknie dialogowym.

## <a name="see-also"></a>Zobacz też

- [Kontrolki ActiveX](/cpp/mfc/activex-controls)
- [Testowanie właściwości i zdarzeń za pomocą kontenera testu](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Debugowanie aplikacji COM i kontrolek ActiveX](../debugger/com-and-activex-debugging.md)
- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)