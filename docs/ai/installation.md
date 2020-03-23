---
title: Instalowanie narzędzi AI
description: W tym artykule opisano sposób instalowania narzędzi AI tools dla programu Visual Studio
keywords: ai, studio wizualne
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: c1160c68c79dd595e82ecf761c6e441ecc906f62
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75915812"
---
# <a name="installation"></a>Instalacja

Narzędzia programu Visual Studio dla AI można zainstalować w 64-bitowych systemach operacyjnych Windows.

## <a name="install-visual-studio-tools-for-ai"></a>Instalowanie narzędzi programu Visual Studio dla aplikacji AI

To rozszerzenie działa z programem Visual Studio 2015 i Visual Studio 2017, wersja społecznościowa lub wyższa.

Narzędzia można pobrać z portalu [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017)lub z programu Visual Studio:

1. Wybierz rozszerzenie**i aktualizacje** **narzędzi** > .

   ![Menu Rozszerzenia i aktualizacje w programie Visual Studio](media/installation/extensions.png)

2. W oknie dialogowym **Rozszerzenia i aktualizacje** wybierz pozycję **Online** po lewej stronie.
3. W polu wyszukiwania w prawym górnym rogu wpisz lub wpisz "narzędzia dla ai".
4. Wybierz **visual studio narzędzia dla ai** z wyników.
5. Kliknij **pozycję Pobierz**.

## <a name="prepare-your-local-machine"></a>Przygotuj swoją lokalną maszynę

Przed szkoleniem modeli uczenia głębokiego na komputerze lokalnym upewnij się, że masz zainstalowane odpowiednie wymagania wstępne. Obejmuje to upewnienie się, że masz najnowsze sterowniki i biblioteki dla swojego procesora graficznego NVIDIA (jeśli go masz). Upewnij się również, że zainstalowano biblioteki Pythona i Pythona, takie jak NumPy, SciPy, oraz odpowiednie struktury uczenia głębokiego, takie jak Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch i Chainer, których zamierzasz używać w Projektu.

> [!NOTE]
> Wprowadzenie oprogramowania w następujących podsekcjach jest zaczerpnięte z ich stron internetowych.

### <a name="nvidia-gpu-driver"></a>Sterownik GPU NVIDIA

Struktury uczenia głębokiego wykorzystują procesor graficzny NVIDIA, aby umożliwić maszynom uczenie się z szybkością, dokładnością i skalowaniem w kierunku prawdziwej sztucznej inteligencji. Jeśli komputer jest zainstalowany na kartach graficznych NVIDIA, zobacz [Pobieranie sterowników NVIDIA](https://www.nvidia.com/Download/index.aspx) lub spróbuj zaktualizować system operacyjny, aby zainstalować najnowszy sterownik.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) to równoległa platforma obliczeniowa i model programowania wynaleziony przez NVIDIĘ. Umożliwia to znaczne zwiększenie wydajności obliczeniowej dzięki wykorzystaniu mocy procesora graficznego. Obecnie CUDA Toolkit 8.0 jest wymagany przez struktury uczenia głębokiego.

Aby zainstalować CUDA

- Odwiedź tę [stronę](https://developer.nvidia.com/cuda-80-ga2-download-archive), pobierz CUDA i zainstaluj ją.
- Upewnij się, że zainstalowano biblioteki środowiska wykonawczego CUDA, a następnie dodaj ścieżkę binarną CUDA do zmiennej środowiskowej %PATH% lub $Path.
- W systemie Windows ta ścieżka jest domyślnie "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

![Instalowanie CUDA w systemie Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN ( cudnn )

[CuDNN](https://developer.nvidia.com/cudnn) (CUDA Deep Neural Network library) to przyspieszona przez GPU biblioteka prymitywów dla głębokich sieci neuronowych firmy NVIDIA. cuDNN v6 jest wymagane przez najnowsze ramy uczenia głębokiego.

Aby zainstalować cuDNN:

- Odwiedź [stronę NVIDIA Developer,](https://developer.nvidia.com/rdp/cudnn-download) aby pobrać i zainstalować najnowszy pakiet.
- Upewnij się, że katalog zawierający plik binarny cuDNN jest zmiennyą środowiskową %PATH% lub $Path.
- W systemie Windows można skopiować cudnn64_6.dll do "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

> [!NOTE]
> Poprzednie struktury uczenia głębokiego, takie jak CNTK 2.0 i TensorFlow 1.2.1, wymagają cuDNN v5.1. Można jednak zainstalować wiele wersji cuDNN razem.

### <a name="python"></a>Python

Python jest podstawowym językiem programowania dla aplikacji uczenia głębokiego. **64-bitowe** Dystrybucja języka Python jest wymagana, a [Python 3.5.4](https://www.python.org/downloads/release/python-354/) jest zalecany dla najlepszej zgodności.

### <a name="to-install-python-on-windows"></a>Aby zainstalować język Python w systemie Windows

- Sugerujemy zainstalowanie uruchamiania Języka Python tylko dla siebie i dodanie Języka Python do zmiennej środowiskowej %PATH%.
- Upewnij się, aby zainstalować pip, który jest system zarządzania pakietami do instalowania i zarządzania pakietami oprogramowania napisanymi w Pythonie.

Struktury uczenia głębokiego opierają się na pip dla własnej instalacji.

![Instalowanie języka Python w systemie Windows](media/installation/install_python_win.png)

Następnie musimy sprawdzić, czy Python 3.5 jest poprawnie zainstalowany, i uaktualnić pip do najnowszej wersji, wykonując następujące polecenia w terminalu:

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **Macos**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Python w programie Visual Studio

Python jest w pełni obsługiwany w programie Visual Studio za pośrednictwem rozszerzeń.
Dowiedz się więcej o [instalowaniu programu Python dla programów Visual Studio Tools,](../python/installing-python-support-in-visual-studio.md) aby uzyskać więcej informacji.

### <a name="numpy-and-scipy"></a>NumPy i SciPy

- **NumPy** to pakiet do przetwarzania tablic ogólnego przeznaczenia, zaprojektowany do efektywnego manipulowania dużymi tablicami wielowymiarowymi dowolnych rekordów bez poświęcania zbyt dużej szybkości dla małych tablic wielowymiarowych.

- **SciPy** (wymawiane "Sigh Pie") jest oprogramowaniem open-source dla matematyki, nauki i inżynierii, w zależności od NumPy. Począwszy od wersji 1.0.0, SciPy ma teraz oficjalny pakiet wstępnie zbudowany koła dla systemu Windows.

Aby zainstalować NumPy i SciPy, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Powyższe polecenie uaktualnia istniejące stare lub nieoficjalne (np. pakiety innych firm z http://www.lfd.uci.edu/~gohlke/pythonlibs/ systemu Windows) NumPy i SciPy do najnowszych oficjalnych.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Zestaw narzędzi usług Microsoft Cognitive (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) to ujednolicony zestaw narzędzi do głębokiego uczenia, który opisuje sieci neuronowe jako serię kroków obliczeniowych za pomocą wykresu kierowanego. CNTK obsługuje zarówno języki programowania Python, jak i BrainScript.

> [!NOTE]
> CNTK obecnie nie obsługuje systemu macOS.

Aby zainstalować pakiet CNTK Python, [zobacz, jak zainstalować program CNTK](/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) to biblioteka oprogramowania typu open source do obliczeń numerycznych przy użyciu wykresów przepływu danych. Szczegółowe informacje na temat instalacji można znaleźć [tutaj.](https://www.tensorflow.org/install/)

> [!NOTE]
> Od wersji 1.2 TensorFlow nie zapewnia już obsługi procesora GPU dla systemu macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) to lekka, modułowa i skalowalna struktura uczenia głębokiego. Opierając się na oryginalnym Caffe, Caffe2 został zaprojektowany z myślą o ekspresji, szybkości i modułowości.

Obecnie nie ma wstępnie utworzonego pakietu kół Caffe2 python.

Odwiedź [tutaj,](https://caffe2.ai/docs/getting-started.html) aby utworzyć z kodu źródłowego.

### <a name="mxnet"></a>MXNet

[Apache MXNet (inkubacja)](https://mxnet.incubator.apache.org/) to struktura uczenia głębokiego zaprojektowana zarówno z myślą o wydajności, jak i elastyczności. Pozwala na **mieszanie** [symboliczne i imperatywne programowanie,](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) aby zmaksymalizować wydajność i produktywność.

Aby zainstalować MXNet, uruchom następujące polecenie w terminalu:

- Z GPU

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- Bez GPU

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) jest interfejsem API sieci neuronowych wysokiego poziomu, napisanym w języku Python, który może działać na szczycie CNTK, TensorFlow lub Theano. Został on opracowany z naciskiem na umożliwienie szybkich eksperymentów. Możliwość przejścia od pomysłu do wyniku z jak najmniejszym opóźnieniem jest kluczem do dobrych badań.

Aby zainstalować keras, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) to biblioteka Pythona, która pozwala na efektywne definiowanie, optymalizowanie i ocenę wyrażeń matematycznych obejmujących tablice wielowymiarowe.

Aby zainstalować Theano, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) to pakiet python, który zapewnia dwie funkcje wysokiego poziomu:

- Obliczenia tensora (jak numpy) z silnym przyspieszeniem GPU
- Głębokie sieci neuronowe zbudowane na systemie autogradu opartym na taśmach

Aby zainstalować pytorch, uruchom następujące polecenie w terminalu:

- **Windows**

  Nie ma jeszcze oficjalnego pakietu kół. Możesz pobrać pakiet innej firmy z [Anaconda](https://anaconda.org/pytorch/repo?type=all) lub [University of California](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch).

  - Dekompresji go do katalogu macierzystego, na przykład *C:\Users\test\pytorch*.
  - Dodaj *C:\Users\test\pytorch\Lib\site-packages* do zmiennej środowiskowej %PYTHONPATH%.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **Macos**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > pliki binarne macOS nie obsługują CUDA, zainstaluj ze źródła, jeśli cuda jest potrzebne

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Ten pojedynczy pakiet obsługuje zarówno procesor graficzny, jak i procesor.

Na koniec zainstaluj torchvision w systemie innych niż Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) to oparta na Pythonie struktura głębokiego uczenia się mająca na celu elastyczność. Zapewnia automatyczne różnicowanie interfejsów API na podstawie podejścia definiowania po uruchomieniu (znany również jako dynamiczne wykresy obliczeniowe), a także obiektowe interfejsy API wysokiego poziomu do tworzenia i szkolenia sieci neuronowych.

Aby włączyć obsługę CUDA, zainstaluj [CuPy:](https://github.com/cupy/cupy)

```bash
pip3.5 install cupy
```

> [!NOTE]
> W systemie Windows potrzebujesz wersji programu [Visual Studio](https://visualstudio.microsoft.com/) 2015 lub [narzędzi kompilacji programu Microsoft Visual C++](https://visualstudio.microsoft.com/visual-cpp-build-tools/) do kompilowania cupy z cuda 8.0.

Aby zainstalować chainer, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install chainer==3.0.0
```
