---
title: Debugowanie kontrolki ActiveX | Microsoft Docs
description: Dowiedz się, jak debugować formant ActiveX. Należy określić zawierający plik wykonywalny, który można wykonać na stronach właściwości projektu lub po rozpoczęciu debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6728b498da91f540d92182ad60f23e490d614948
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160398"
---
# <a name="how-to-debug-an-activex-control"></a>Porady: debugowanie formantu ActiveX

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Aby debugować formant ActiveX, należy określić kontener (plik wykonywalny), w którym ma zostać uruchomiony formant.

## <a name="to-specify-a-container-for-the-debug-session"></a>Aby określić kontener dla sesji debugowania

1. W Eksplorator rozwiązań wybierz projekt.

2. Z menu **Widok** wybierz polecenie **strony właściwości**.

3. W oknie dialogowym **strony właściwości projektu** Otwórz folder **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie**.

4. W kategorii **debugowanie** Znajdź właściwość **polecenie** .

5. Określ nazwę ścieżki dla kontenera. Na przykład C:\Program Files\Internet Explorer\IEXPLORE.EXE.

6. W przypadku określenia programu Internet Explorer jako kontenera i używania programu Active Desktop wpisz `/new` w polu **argumenty polecenia** .

7. Kliknij przycisk **OK**.

     Jeśli nie określisz kontenera w oknie dialogowym **strony właściwości projektu** , możesz określić kontener po rozpoczęciu debugowania. Po wybraniu polecenia wykonywania w celu rozpoczęcia debugowania zostanie wyświetlone okno [dialogowe plik wykonywalny dla sesji debugowania](../debugger/executable-for-debugging-session-dialog-box.md) . Określ nazwę ścieżki kontenera w oknie dialogowym.

## <a name="see-also"></a>Zobacz też

- [Kontrolki ActiveX](/cpp/mfc/activex-controls)
- [Testowanie właściwości i zdarzeń za pomocą kontenera testów](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Debugowanie modelu COM i ActiveX](../debugger/com-and-activex-debugging.md)
- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
