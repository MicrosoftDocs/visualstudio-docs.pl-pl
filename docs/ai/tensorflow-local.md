---
title: Lokalne uczenie modelu tensorflow
description: Uruchamianie modelu tensorflow lokalnie w narzędziach AI Tools for Visual Studio
keywords: AI, Visual Studio, tensorflow, Local
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 0ceb21701958630c8b783d5b6850c5e0a0ab229a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841383"
---
# <a name="train-a-tensorflow-model-locally"></a>Lokalne uczenie modelu TensorFlow

W tym przewodniku szybki start poprowadzimy model TensorFlow z zestawem danych [mnist ręcznie](http://yann.lecun.com/exdb/mnist/) lokalnie w Visual Studio Tools for AI.

Baza danych MNIST ręcznie ma zestaw szkoleniowy 60 000 przykładów oraz zestaw testów 10 000 cyfr odręcznych.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem upewnij się, że zainstalowano następujące elementy:

### <a name="google-tensorflow"></a>Google TensorFlow

Uruchom następujące polecenie w terminalu:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy i SciPy
Zainstaluj [numpy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) i [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Pobierz przykładowy kod
Pobierz to [repozytorium GitHub](https://github.com/Microsoft/samples-for-ai) zawierające przykłady umożliwiające wprowadzenie do uczenia głębokiego w ramach usługi TENSORFLOW, CNTK, Theano i innych.

## <a name="open-solution-and-train-model"></a>Otwórz rozwiązanie i model uczenia

- Uruchom program Visual Studio i wybierz pozycję **plik > otwórz > projektu/rozwiązania**.

- Wybierz folder **przykładów Tensorflow** z pobranego repozytorium Samples i Otwórz plik **TensorflowExamples. sln** .

   ![Otwieranie projektu](media/tensorflow-local/open-project.png)

   ![Otwórz rozwiązanie](media/tensorflow-local/open-solution.png)

- Znajdź projekt MNIST ręcznie w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy i wybierz pozycję **Ustaw jako projekt startowy**.

- Kliknij przycisk **Uruchom**.

- Dane wyjściowe są drukowane w konsoli programu.

   ![Przykładowe dane wyjściowe z konsoli](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Trenowanie modelu TensorFlow w chmurze](tensorflow-vm.md)
