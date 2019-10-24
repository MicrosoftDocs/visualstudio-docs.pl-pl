---
title: Zainstaluj narzędzia AI
description: Opisuje sposób instalowania narzędzi AI Tools for Visual Studio
keywords: AI, Visual Studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: fb296346d54b0774bdd9a738581ee28fe99b1de0
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777469"
---
# <a name="installation"></a>Instalacja

Visual Studio Tools for AI można zainstalować w systemach operacyjnych Windows 64-bitowych.

## <a name="install-visual-studio-tools-for-ai"></a>Zainstaluj Visual Studio Tools for AI

To rozszerzenie współpracuje z programem Visual Studio 2015 i Visual Studio 2017, wersja Community lub nowsza.

Narzędzia można pobrać z [Visual Studio Marketplace](https://aka.ms/vstoolsforai)lub z poziomu programu Visual Studio:

1. Wybierz pozycję **narzędzia**  > **rozszerzenia i aktualizacje**.

   ![Menu rozszerzenia i aktualizacje w programie Visual Studio](media/installation/extensions.png)

2. W oknie dialogowym **rozszerzenia i aktualizacje** wybierz pozycję **online** po lewej stronie.
3. W polu wyszukiwania w prawym górnym rogu wpisz lub wprowadź "Tools for AI".
4. Wybierz **Visual Studio Tools for AI** z wyników.
5. Kliknij przycisk **Pobierz**.

## <a name="prepare-your-local-machine"></a>Przygotowywanie komputera lokalnego

Przed rozpoczęciem szkolenia modeli uczenia głębokiego na komputerze lokalnym upewnij się, że zainstalowano odpowiednie wymagania wstępne. Obejmuje to zapewnienie, że masz najnowsze sterowniki i biblioteki dla procesora GPU NVIDIA (jeśli istnieje). Upewnij się również, że zainstalowano biblioteki Python i Python, takie jak NumPy, SciPy i odpowiednie platformy uczenia głębokiego, takie jak Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch i łańcucha, które planujesz używać w projektu.

> [!NOTE]
> Wprowadzenie oprogramowania w poniższych podsekcjach jest podano na podstawie ich strony główne.

### <a name="nvidia-gpu-driver"></a>Sterownik procesora GPU NVIDIA

Platformy uczenia głębokiego korzystają z technologii NVIDIA GPU, aby umożliwić maszynom uczenie się o szybkości, dokładności i skalowaniu w kierunku prawdziwej sztucznej analizy. Jeśli komputer ma karty graficzne procesora NVIDIA, zobacz artykuł [sterowniki firmy NVIDIA — pliki do pobrania](https://www.nvidia.com/Download/index.aspx) lub wypróbuj aktualizację systemu operacyjnego w celu zainstalowania najnowszego sterownika.

### <a name="cuda"></a>CUDA

[Cuda](https://developer.nvidia.com/cuda-zone) to równoległa platforma obliczeniowa i model programowania stworzone przez firmy NVIDIA. Zapewnia znaczący wzrost wydajności obliczeniowej przez wykorzystanie mocy procesora GPU. Obecnie narzędzia CUDA toolkit 8,0 są wymagane przez platformy uczenia głębokiego.

Aby zainstalować CUDA

- Odwiedź tę [witrynę](https://developer.nvidia.com/cuda-80-ga2-download-archive), Pobierz cuda i zainstaluj ją.
- Upewnij się, że zainstalowano biblioteki środowiska uruchomieniowego CUDA, a następnie dodaj ścieżkę binarną CUDA do zmiennej środowiskowej% PATH% lub $Path.
- W systemie Windows ta ścieżka jest domyślnie "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

![Zainstaluj program CUDA w systemie Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (cuda głęboka biblioteka sieciowa neuronowych) to przyspieszona w procesorze GPU Biblioteka elementów podstawowych dla głębokiej sieci neuronowych przez NVIDIA. cuDNN v6 jest wymagana przez najnowsze platformy uczenia głębokiego.

Aby zainstalować cuDNN:

- Odwiedź stronę [NVIDIA Developer](https://developer.nvidia.com/rdp/cudnn-download) , aby pobrać i zainstalować najnowszy pakiet.
- Upewnij się, że dodano katalog zawierający plik binarny cuDNN do zmiennej środowiskowej% PATH% lub $Path.
- W systemie Windows można skopiować cudnn64_6. dll do lokalizacji "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

> [!NOTE]
> Wcześniejsze platformy uczenia głębokiego, takie jak CNTK 2,0 i TensorFlow 1.2.1, potrzebują cuDNN v 5.1. Można jednak zainstalować wiele wersji cuDNN.

### <a name="python"></a>Python

Język Python jest głównym języku programowania aplikacji do uczenia głębokiego. **64 — bit** Wymagana jest dystrybucja języka Python, a w celu uzyskania najlepszej zgodności zalecamy używanie języka [Python 3.5.4](https://www.python.org/downloads/release/python-354/) .

### <a name="to-install-python-on-windows"></a>Aby zainstalować język Python w systemie Windows

- Zalecamy zainstalowanie modułu uruchamiania języka Python tylko dla siebie i dodanie języka Python do zmiennej środowiskowej% PATH%.
- Upewnij się, że instalujesz program PIP, który jest system zarządzania pakietami, aby instalować i zarządzać pakietami oprogramowania zapisanymi w języku Python.

Platformy uczenia głębokiego są zależne od PIP na potrzeby własnej instalacji.

![Instalowanie języka Python w systemie Windows](media/installation/install_python_win.png)

Następnie musimy sprawdzić, czy środowisko Python 3,5 zostało poprawnie zainstalowane, a następnie Uaktualnij program PIP do najnowszej wersji, wykonując następujące polecenia w terminalu:

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

### <a name="python-on-visual-studio"></a>Język Python w programie Visual Studio

Środowisko Python jest w pełni obsługiwane w programie Visual Studio przez rozszerzenia.
Dowiedz się więcej o instalowaniu języka [Python dla Visual Studio Tools](../python/installing-python-support-in-visual-studio.md) , aby uzyskać więcej informacji.

### <a name="numpy-and-scipy"></a>NumPy i SciPy

- **Numpy** to pakiet przetwarzania tablicowego ogólnego przeznaczenia zaprojektowany w celu wydajnego manipulowania wielowymiarowymi tablicami dowolnych rekordów bez pogorszenia zbyt dużej szybkości dla małych wielowymiarowych tablic.

- **SciPy** (wymawiane "sigh kołowe") to oprogramowanie typu "open source" służące do nauki, nauki i inżynierii, w zależności od numpy. Począwszy od wersji 1.0.0, SciPy ma teraz oficjalnego prekompilowanego pakietu dla systemu Windows.

Aby zainstalować NumPy i SciPy, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Powyższe polecenie uaktualnia istniejący stary lub nieoficjalny (np. pakiety innych firm z http://www.lfd.uci.edu/~gohlke/pythonlibs/ dla systemu Windows) NumPy i SciPy do najnowszych oficjalnych.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) to ujednolicony zestaw narzędzi głębokiego uczenia, który opisuje sieci neuronowych jako serię etapów obliczeniowych za pośrednictwem ukierunkowanego wykresu. CNTK obsługuje języki programowania w języku Python i BrainScript.

> [!NOTE]
> CNTK obecnie nie obsługuje macOS.

Aby zainstalować pakiet CNTK Python, zobacz [How to Install CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) to Biblioteka oprogramowania Open Source służąca do obliczania liczbowego przy użyciu wykresów przepływu danych. Zobacz [tutaj](https://www.tensorflow.org/install/) , aby zapoznać się ze szczegółową instalacją.

> [!NOTE]
> Począwszy od wersji 1,2, TensorFlow nie zapewnia już obsługi procesora GPU dla macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) to uproszczona, modularna i skalowalna platforma uczenia głębokiego. Kompilowanie na oryginalne Caffe, Caffe2 jest zaprojektowana z uwzględnieniem wyrażeń, szybkości i modularności.

Obecnie nie ma dostępnego prekompilowanego pakietu Caffe2 języka Python.

Odwiedź [tutaj](https://caffe2.ai/docs/getting-started.html) , aby skompilować kod źródłowy.

### <a name="mxnet"></a>MXNet

[Apache MXNet (inkubacja)](https://mxnet.incubator.apache.org/) to platforma uczenia głębokiego, zaprojektowana pod kątem wydajności i elastyczności. Pozwala to na **mieszanie** [symbolicznych i](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) bezwzględnych programów w celu zmaksymalizowania wydajności i wydajności.

Aby zainstalować MXNet, uruchom następujące polecenie w terminalu:

- Z procesorem GPU

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- Bez procesora GPU

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) to interfejs API sieci neuronowych wysokiego poziomu, zapisany w języku Python, który może działać w oparciu o CNTK, TensorFlow lub Theano. Został zaprojektowany z myślą o umożliwieniu szybkiego eksperymentowania. Możliwość przechodzenia z pomysłu w celu uzyskania najmniejszego możliwego opóźnienia jest kluczem do wykonywania dobrych badań.

Aby zainstalować Keras, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) to biblioteka języka Python, która umożliwia definiowanie, optymalizowanie i ocenę wyrażeń matematycznych w celu wydajnej obsługi tablic wielowymiarowych.

Aby zainstalować Theano, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) to pakiet języka Python, który udostępnia dwie funkcje wysokiego poziomu:

- Obliczanie dwuskładnikowe (na przykład numpy) z silnym przyspieszeniem GPU
- Głębokie sieci neuronowych oparte na taśmach systemu o podwójnej klasyfikacji

Aby zainstalować PyTorch, uruchom następujące polecenie w terminalu:

- **Windows**

  Nie istnieje jeszcze urzędowy pakiet kół. Pakiet innej firmy można pobrać z [Anaconda](https://anaconda.org/pytorch/repo?type=all) lub [University of California](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch).

  - Dekompresuj je do katalogu macierzystego, na przykład *C:\Users\test\pytorch*.
  - Dodaj *C:\Users\test\pytorch\Lib\site-Packages* do zmiennej środowiskowej% PYTHONPATH%.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **macOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > pliki binarne macOS nie obsługują CUDA, Instaluj ze źródła, jeśli jest potrzebny CUDA

- **System**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Ten pojedynczy pakiet obsługuje procesor GPU i procesor CPU.

Na koniec Zainstaluj program torchvision w systemie innym niż Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Łańcucha](https://chainer.org/) to platforma uczenia głębokiego oparta na języku Python, która ma na celu elastyczność. Zapewnia ona automatyczne różnicowe interfejsy API oparte na podejściu Definiuj-by-Run (nazywanego również dynamicznymi wykresami obliczeniowymi) oraz opartych na obiektach interfejsów API wysokiego poziomu do kompilowania i uczenia sieci neuronowych.

Aby włączyć obsługę CUDA, zainstaluj [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> W systemie Windows potrzebna jest wersja 2015 programu [Visual Studio](https://visualstudio.microsoft.com/) lub [narzędzia Microsoft C++ Visual Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) , aby kompilować CuPy z cuda 8,0.

Aby zainstalować moduł łańcucha, uruchom następujące polecenie w terminalu:

```bash
pip3.5 install chainer==3.0.0
```
