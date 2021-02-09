---
title: Przełączanie na inny wątek w trakcie debugowania
description: Przejrzyj różne metody, aby przełączyć się do innego wątku podczas debugowania aplikacji wielowątkowej w programie Visual Studio.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: affc4dec196169580ff23c5faf2f7876a71fbba9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896516"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Instrukcje: przełączanie do innego wątku podczas debugowania w programie Visual Studio (C#, Visual Basic, C++)
Podczas debugowania aplikacji wielowątkowej można użyć dowolnej z kilku metod, aby przełączyć się z wątku, z którym pracujesz w innym wątku.

> [!NOTE]
> Jeśli chcesz kontrolować kolejność wykonywania wątków, należy [zablokować i odblokować wątki](../debugger/get-started-debugging-multithreaded-apps.md).

Gdy badasz wątki w edytorze kodu i różne okna debugowania wielowątkowego, żółta strzałka wskazuje bieżący wątek. Zielona strzałka z ogonem klamrowym wskazuje, że wątek inny niż bieżący ma bieżący kontekst debugera.

### <a name="to-switch-to-any-thread-that-appears"></a>Aby przełączyć się na dowolny wątek, który pojawia się

- W oknie **wątki** lub **równoległe polecenie Watch** kliknij dwukrotnie wątek.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Aby przełączyć się do wątku w oknie źródłowym

- Na lewym marginesie kliknij prawym przyciskiem myszy ![znacznik](../debugger/media/dbg-thread-marker.png "ThreadMarker")wątku ikony znacznika, wskaż polecenie **Przełącz do**, a następnie kliknij nazwę tego wątku, do którego chcesz się przełączyć. Menu skrótów zawiera tylko wątki w tym konkretnym miejscu.

     Jeśli nie ma żadnych znaczników wątków, kliknij prawym przyciskiem myszy w oknie **wątki** i sprawdź, czy wybrano opcję **Pokaż wątki w źródle** .

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Aby przełączyć się do wątku na pasku narzędzi lokalizacji debugowania

1. Na pasku narzędzi **Lokalizacja debugowania** kliknij listę **wątek** .

2. Na liście kliknij wątek, do którego chcesz się przełączyć.

## <a name="see-also"></a>Zobacz też
- [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)
