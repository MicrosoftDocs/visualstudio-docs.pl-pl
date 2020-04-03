---
title: Trenuj model tensorflow lokalnie
description: Uruchamianie modelu tensorflow lokalnie w programie AI Tools for Visual Studio
keywords: ai, studio wizualne, tensorflow, lokalne
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: eca02b74154eab5468adeabdb84efdf2839fc92e
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638742"
---
# <a name="train-a-tensorflow-model-locally"></a>Trenuj model TensorFlow lokalnie

W tym przewodniku Szybki start będziemy szkolić model TensorFlow z zestawem danych [MNIST](http://yann.lecun.com/exdb/mnist/) lokalnie w programie Visual Studio Tools for AI.

Baza danych MNIST ma zestaw szkoleniowy 60 000 przykładów i zestaw testów zawierający 10 000 przykładów cyfr odręcznych.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz zainstalowane następujące elementy:

### <a name="google-tensorflow"></a>Google TensorFlow

Uruchom następujące polecenie w terminalu:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy i SciPy
Zainstaluj [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) i [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Pobierz przykładowy kod
Pobierz to [repozytorium GitHub](https://github.com/Microsoft/samples-for-ai) zawierające przykłady do rozpoczęcia nauki głębokiej w TensorFlow, CNTK, Theano i innych.

## <a name="open-solution-and-train-model"></a>Otwórz rozwiązanie i model pociągu

- Uruchom program Visual Studio i wybierz **opcję > otwórz > projekt/rozwiązanie**.

- Wybierz folder **Tensorflow Examples** z pobranego repozytorium próbek i otwórz plik **TensorflowExamples.sln.**

   ![Otwieranie projektu](media/tensorflow-local/open-project.png)

   ![Otwarte rozwiązanie](media/tensorflow-local/open-solution.png)

- Znajdź projekt MNIST w **Eksploratorze rozwiązań**, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw jako projekt startowy**.

- Kliknij przycisk **Uruchom**.

- Dane wyjściowe są drukowane w konsoli.

   ![Przykładowe dane wyjściowe z konsoli](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Trenuj model TensorFlow w chmurze](tensorflow-vm.md)
