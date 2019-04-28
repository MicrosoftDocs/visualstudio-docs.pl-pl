---
title: Zainstaluj narzędzia SI
description: W tym artykule opisano sposób instalowania narzędzia sztucznej Inteligencji dla programu Visual Studio
keywords: sztuczna inteligencja, program visual studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 623aa21e94ff25b8190bae82ca836ed16f64bcaa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548450"
---
# <a name="installation"></a>Instalacja

Visual Studio Tools for AI można zainstalować w systemach operacyjnych Windows 64-bitowych.

## <a name="install-visual-studio-tools-for-ai"></a>Install Visual Studio Tools for AI

To rozszerzenie działa przy użyciu programu Visual Studio 2015 i Visual Studio 2017 Community edition lub nowszy.

Możesz pobrać narzędzia z [Visual Studio Marketplace](https://aka.ms/vstoolsforai), lub z poziomu programu Visual Studio:

1. Wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

   ![Menu rozszerzenia i aktualizacje w programie Visual Studio](media/installation/extensions.png)

2. W **rozszerzenia i aktualizacje** okno dialogowe, wybierz opcję **Online** po lewej stronie.
3. W polu wyszukiwania w prawym górnym rogu wpisz lub wprowadź "tools for ai".
4. Wybierz **Visual Studio Tools for AI** z wyników.
5. Kliknij przycisk **Pobierz**.

## <a name="prepare-your-local-machine"></a>Przygotowanie komputera lokalnego

Przed szkolenia głębokiego uczenia modeli na komputerze lokalnym, upewnij się, że masz zainstalowane odpowiednie wymagania wstępne. Dotyczy to również, upewniając się, że masz najnowsze sterowniki i biblioteki dla procesor GPU NVIDIA (jeśli istnieje). Należy również upewnić się, możesz został zainstalowany język Python i środowiska Python biblioteki, takie jak NumPy SciPy i odpowiednich platform, takich jak Microsoft Cognitive Toolkit (CNTK), Keras, TensorFlow, MXNet, Theano, Caffe2, PyTorch i Chainer, który ma być używany w do uczenia głębokiego Projekt.

> [!NOTE]
> Wprowadzenie oprogramowania w następujących podsekcjach jest wyszczególniony z ich strony główne.

### <a name="nvidia-gpu-driver"></a>Sterownik procesora GPU NVIDIA

Platformy uczenia głębokiego zalet procesor GPU NVIDIA umożliwiające maszyn, Dowiedz się więcej z prędkością, dokładności i skalowanie na wartość true, sztucznej inteligencji. Jeśli komputer ma karty procesorów GPU firmy NVIDIA, odwiedź stronę [tutaj](http://www.nvidia.com/Download/index.aspx) lub spróbuj aktualizacji systemu operacyjnego, aby zainstalować najnowszy sterownik.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) jest równoległych obliczeń platformy i stworzone przez procesory GPU NVIDIA model programowania. Dzięki temu znaczący wzrost przetwarzania danych wydajności przez wykorzystywanie możliwości procesora GPU. Obecnie CUDA Toolkit 8.0 jest wymagana przez platformy uczenia głębokiego.

Aby zainstalować CUDA

- Odwiedź witrynę [witryny](https://developer.nvidia.com/cuda-80-ga2-download-archive), CUDA Pobierz i zainstaluj go.
- Upewnij się, że instalacji bibliotek środowiska uruchomieniowego CUDA, a następnie dodaj binarne ścieżki CUDA, aby % % lub $Path zmiennej środowiskowej PATH.
- W Windows ta ścieżka jest "C:\Program Files\NVIDIA GPU obliczeń Toolkit\CUDA\v8.0\bin" domyślnie.

![Zainstaluj CUDA na Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (głębokie sieci neuronowe CUDA library) to biblioteka pierwotne wartości głębokich sieciach neuronowych przez procesory GPU NVIDIA accelerated procesora GPU. cuDNN w wersji 6 jest wymagana przez najnowsze platformy uczenia głębokiego.

Aby zainstalować cuDNN:

- Odwiedź stronę [dla deweloperów firmy NVIDIA](https://developer.nvidia.com/rdp/cudnn-download) do pobrania i zainstalowania najnowszego pakietu.
- Upewnij się, aby dodać do katalogu zawierającego cuDNN binarnego % % lub $Path zmiennej środowiskowej PATH.
- W Windows można skopiować cudnn64_6.dll do "C:\Program Files\NVIDIA GPU obliczeń Toolkit\CUDA\v8.0\bin".

> [!NOTE]
> Poprzednie platformy uczenia głębokiego, takie jak CNTK w wersji 2.0 i TensorFlow 1.2.1 muszą cuDNN v5.1. Można jednak zainstalować wiele wersji cuDNN ze sobą.

### <a name="python"></a>Python

Python został podstawowy język programowania przeznaczony dla aplikacji do uczenia głębokiego. **64-bitowych** dystrybucji Python jest wymagana, i [Python 3.5.4](https://www.python.org/downloads/release/python-354/) zaleca się pod kątem zgodności.

### <a name="to-install-python-on-windows"></a>Do zainstalowania języka Python na Windows

- Firma Microsoft sugeruje tylko instalowanie uruchamianie języka Python dla siebie i język Python został dodany do zmiennej środowiskowej % PATH %.
- Upewnij się, aby zainstalować narzędzia pip, czyli system zarządzania pakietami instalacji i zarządzaniu pakietów oprogramowania napisane w języku Python.

Platformy uczenia głębokiego, zależą od narzędzie pip dla ich własnych instalacji.

![Instalowanie języka Python w Windows](media/installation/install_python_win.png)

Następnie należy sprawdzić, czy prawidłowo zainstalowano język Python 3.5 i uaktualnić pakiet pip do najnowszej wersji, wykonując następujące polecenia w terminalu:

- **Windows**

    ```cmd
    C:\Users\test>python -V
    Python 3.5.4

    C:\Users\test>pip3.5 -V
    pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

    C:\Users\test>python -m pip install -U pip
    ```

- **macOS**

    ```bash
    MyMac:~ test$ python3.5 -V
    Python 3.5.4

    MyMac:~ test$ pip3.5 -V
    pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

    MyMac:~ test$ python3.5 -m pip install -U pip
    ```

### <a name="python-on-visual-studio"></a>Python w programie Visual Studio

Python jest w pełni obsługiwany w programie Visual Studio za pośrednictwem rozszerzeń.
Dowiedz się więcej na temat instalacji [języka Python dla programu Visual Studio Tools](../python/installing-python-support-in-visual-studio.md) Aby uzyskać więcej informacji.

### <a name="numpy-and-scipy"></a>NumPy i SciPy

- **NumPy** jest zaprojektowany do wydajnego manipulowania duże tablice wielowymiarowe dowolnych rekordów bez obniżania oczekiwanego poziomu zbyt dużo szybkość dla małych Wielowymiarowe tablice ogólnego przeznaczenia pakiet przetwarzania tablicy.

- **SciPy** (wymawiane "Sigh kołowy") to oprogramowanie typu open source, matematyki, nauki i inżynierii, w zależności od NumPy. Począwszy od wersji 1.0.0, SciPy ma teraz pakiet wheel wbudowanych oficjalne dla Windows.

Aby zainstalować NumPy i SciPy, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Powyżej uaktualnień polecenia istniejących starych lub nieoficjalny (np. pakietów innych firm z http://www.lfd.uci.edu/~gohlke/pythonlibs/ for Windows) NumPy i SciPy najnowsze te oficjalnych.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) to ujednolicone narzędzi uczenia głębokiego, opisywanie sieci neuronowych jako serię etapów obliczeniowych za pomocą wykresu bezpośredniego. CNTK obsługuje zarówno języka Python i BrainScript języków programowania.

> [!NOTE]
> CNTK aktualnie nie obsługuje systemu macOS.

Aby zainstalować pakiet języka Python CNTK, zobacz [sposobu instalowania CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) jest biblioteka oprogramowania typu open source umożliwiająca wykonywanie obliczeń numerycznych przy użyciu wykresów przepływu danych. Zapoznaj się [tutaj](https://www.tensorflow.org/install/) szczegółowe instalacji.

> [!NOTE]
> Począwszy od wersji 1.2 TensorFlow już nie obsługuje procesora GPU dla systemu macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) to struktura lekka, modularna i skalowalna uczenia głębokiego. Opierając się na oryginalnej Caffe, Caffe2 została zaprojektowana pod kątem wyrażenia, szybkość i Modułowość na uwadze.

Obecnie nie ma żadnych wbudowanych pakiet wheel języka python Caffe2 dostępne.

Odwiedź stronę [tutaj](https://caffe2.ai/docs/getting-started.html) tworzenie z kodu źródłowego.

### <a name="mxnet"></a>MXNet

[Apache MXNet (wersja inkubacyjna)](https://mxnet.incubator.apache.org/) to platforma uczenia głębokiego, przeznaczony dla środowisk wydajność i elastyczność. Umożliwia on **mieszać** [programowania symboliczne i bezwzględne](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) Aby zmaksymalizować wydajność i produktywność.

Aby zainstalować MXNet, uruchom następujące polecenie w terminalu:

- Przy użyciu procesora GPU

    ```bash
    pip3.5 install mxnet-cu80==0.12.0
    ```

- Bez procesora GPU

    ```bash
    pip3.5 install mxnet==0.12.0
    ```

### <a name="keras"></a>Biblioteki Keras

[Biblioteki Keras](https://keras.io/) to interfejs API sieci neuronowych wysokiego poziomu, napisany w języku Python i stanie działać u góry, CNTK, TensorFlow lub Theano. Został on opracowany ze szczególnym uwzględnieniem umożliwiające szybkie eksperymentowania. Możliwość przejść od pomysłu do wyniku o najniższe możliwe opóźnienie to klucz do badań dobry sposób.

Aby zainstalować biblioteki Keras, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) to biblioteka języka Python, która umożliwia definiowanie, optymalizowanie i oceny wyrażenia matematyczne, efektywnie obejmujące tablic wielowymiarowych.

Aby zainstalować Theano, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](http://pytorch.org/) to pakiet języka python, który zapewnia dwie funkcje wysokiego poziomu:

- Obliczenie tensor (na przykład numpy) za pomocą silnych przyspieszenie procesora GPU
- Głębokie sieci neuronowe oparty na systemie autograd opartej na taśmach

Aby zainstalować PyTorch, uruchom następujące polecenie w terminalu:

- **Windows**

   Istnieje jeszcze nie pakiet wheel oficjalnych. Możesz pobrać pakiet innych firm z [Anaconda](https://anaconda.org/pytorch/repo?type=all) lub [uniwersytet kalifornijski](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch).

   - Na przykład Dekompresuj do katalogu macierzystego, *C:\Users\test\pytorch*.
   - Dodaj *C:\Users\test\pytorch\Lib\site-packages* Aby zmienna środowiskowa % PYTHONPATH %.

      ```bash
      pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
      pip3 install torchvision
      ```

- **macOS**

    ```bash
    pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
    ```

    > [!NOTE]
    > pliki binarne systemu macOS nie obsługuje CUDA, zainstaluj ze źródła, jeśli jest potrzebny CUDA

- **Linux**

    ```bash
    pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
    ```

    > [!NOTE]
    > Pojedynczy pakiet obsługuje zarówno procesorów GPU i CPU.

Na koniec Zainstaluj torchvision na inne niż Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) to architektura oparta na środowisku Python uczenia głębokiego zmierzających elastyczność. Umożliwia automatyczne różnice między interfejsów API opartych na **podejście zdefiniować przez uruchomienie** (zwane) dynamiczne wykresy obliczeniowe) oraz zorientowane obiektowo interfejsy API wysokiego poziomu do tworzenia i uczenie sieci neuronowych.

Aby włączyć obsługę architektury CUDA, należy zainstalować [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> W Windows, potrzebujesz wersji 2015 [programu Visual Studio](https://visualstudio.microsoft.com/) lub [Microsoft narzędzia Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) skompilować CuPy z CUDA 8.0.

Aby zainstalować moduł łańcucha, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install chainer==3.0.0
```