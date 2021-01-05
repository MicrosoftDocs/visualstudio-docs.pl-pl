---
title: Monitoruj przy użyciu TensorBoard
description: Dowiedz się, jak za pomocą programu Visual Studio wizualizować postęp szkolenia modelu za pomocą TensorBoard.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 650189c4418355ae06b296bac7e16eece0ea88ad
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727258"
---
# <a name="monitor-with-tensorboard"></a>Monitoruj przy użyciu TensorBoard

Możesz wizualizować postęp szkolenia modelu za pomocą TensorBoard.

1. Kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Uruchom TensorBoard**; następnie wybierz katalog wyjściowych dzienników TensorBoard.

    ![Zrzut ekranu programu Visual Studio Eksplorator rozwiązań z wybranym projektem MNIST ręcznie. Menu kontekstowe jest otwarte i jest zaznaczone polecenie Uruchom TensorBoard.](media/monitor-tensorboard/run-tensorboard.png)

2. Zwróć uwagę na to, że błąd zmniejsza się w miarę upływu czasu, co oznacza zwiększenie jakości.

    ![Zrzut ekranu przedstawiający okno główne TensorBoard z graficznymi wizualizacjami danych z dzienników TensorBoard.](media/monitor-tensorboard/tensorboard.png)
