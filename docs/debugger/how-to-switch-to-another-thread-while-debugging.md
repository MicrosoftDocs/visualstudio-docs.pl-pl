---
title: Przełączanie na inny wątek w trakcie debugowania
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5a8fd2106d4982f8e840974bc659d2296cf8c592
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227528"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Instrukcje: Przełączanie na inny wątek w trakcie debugowania w programie Visual Studio (C#, Visual Basic, C++)
Podczas debugowania aplikacji wielowątkowych, można użyć jednego z kilku metod, aby przełączyć się z wątku, który odbywała się wcześniej Praca z do innego wątku.

> [!NOTE]
> Jeśli chcesz kontrolować kolejność, w którym wykonywanie wątków, musisz [Zablokuj i Odblokuj wątki](../debugger/get-started-debugging-multithreaded-apps.md).

Żółta strzałka wskazuje bieżący wątek, podczas badania wątków w edytorze kodu i różnych wielowątkowe debugowanie systemu windows. Zielona strzałka z zakręconym ogonkiem wskazuje, czy innym niż bieżący wątek jest bieżący kontekst debugera.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Aby przełączyć się do dowolnego wątku, który pojawia się 
  
-   W **wątków** lub **równoległego wyrażenia kontrolnego** okna, kliknij dwukrotnie wątek.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Aby przełączyć się do wątku w oknie źródła  
  
-   Na lewym marginesie, kliknij prawym przyciskiem myszy ikonę znacznika wątku ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker"), wskaż polecenie **przełączyć się do**, a następnie kliknij nazwę tego wątku, do którego chcesz się przełączyć . Menu skrótów pokazuje tylko wątków w tej konkretnej lokalizacji.  
  
     Jeśli są wyświetlane bez znaczników do wątku, kliknij prawym przyciskiem myszy **wątków** okna i sprawdź, czy **Pokaż wątki w źródle** jest zaznaczone.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Aby przełączyć się do wątku w pasku narzędzi debugowania lokalizacji  
  
1.  Na **Lokalizacja debugowania** narzędzi, kliknij przycisk **wątku** listy.  
  
2.  Na liście kliknij wątku, do którego chcesz się przełączyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
