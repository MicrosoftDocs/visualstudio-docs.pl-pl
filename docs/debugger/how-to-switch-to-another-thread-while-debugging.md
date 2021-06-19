---
title: Przełączanie na inny wątek w trakcie debugowania
description: Przejrzyj różne metody przełączania do innego wątku podczas debugowania aplikacji wielowątkowej w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a0a68047c5c9e772fc978c56f2cd70dc9454ca57
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384697"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>How to: Switch to Another Thread While Debugging in Visual Studio (C#, Visual Basic, C++)
Podczas debugowania aplikacji wielowątkowej można użyć dowolnej z kilku metod, aby przełączyć się z wątku, z którym pracujesz, na inny wątek.

> [!NOTE]
> Jeśli chcesz kontrolować kolejność wykonywania wątków, musisz zablokować i [pognieć wątki](../debugger/get-started-debugging-multithreaded-apps.md).

Podczas badania wątków w edytorze kodu i różnych oknach debugowania wielowątkowego żółta strzałka wskazuje bieżący wątek. Zielona strzałka ze zwiniętym ogonem wskazuje, że bieżący wątek ma bieżący kontekst debugera.

### <a name="to-switch-to-any-thread-that-appears"></a>Aby przełączyć się do dowolnego wyświetlonego wątku

- W **oknie Wątki** **lub Równoległe śledzenie** kliknij dwukrotnie wątek.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Aby przełączyć się do wątku w oknie źródła

- W lewym rynnie kliknij prawym przyciskiem myszy ikonę znacznika wątku ![Znacznik](../debugger/media/dbg-thread-marker.png "ThreadMarker")wątku, wskaż polecenie Przełącz na **,** a następnie kliknij nazwę tego wątku, na który chcesz przełączyć. Menu skrótów pokazuje tylko wątki w tej określonej lokalizacji.

     Jeśli nie zostaną wyświetlone żadne znaczniki wątku, kliknij prawym przyciskiem myszy w oknie **Wątki** i sprawdź, czy wybrano opcję **Pokaż wątki w** źródle.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Aby przełączyć się do wątku na pasku narzędzi Lokalizacja debugowania

1. Na pasku **narzędzi Lokalizacja debugowania** kliknij listę **Wątek.**

2. Na liście kliknij wątek, do którego chcesz się przełączyć.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
