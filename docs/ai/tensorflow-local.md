---
title: Trenuj model tensorflow lokalnie
description: Uruchamianie modelu tensorflow lokalnie w programie AI Tools for Visual Studio
keywords: ai, studio wizualne, tensorflow, lokalne
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 43ce126baeb96efcaab3c40bac912274ee1cd8c7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72777428"
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
