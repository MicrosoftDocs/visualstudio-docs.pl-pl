---
title: Uruchamianie modelu TensorFlow w chmurze
description: Uruchamianie modelu tensorflow na maszynie wirtualnej uczenie głębokie Azure
keywords: Maszyna wirtualna AI, Visual Studio, uczenie głębokie
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 6cd833a687591ba4f49e785746381f9a5d738f5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80638755"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Trenowanie modelu TensorFlow w chmurze

W tym samouczku będziemy przeszkolić model TensorFlow przy użyciu [zestawu danych mnist ręcznie](http://yann.lecun.com/exdb/mnist/) na maszynie wirtualnej usługi Azure [głębokiej uczenie](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) .

Baza danych MNIST ręcznie ma zestaw szkoleniowy 60 000 przykładów oraz zestaw testów 10 000 cyfr odręcznych.

## <a name="prerequisites"></a>Wymagania wstępne
Przed rozpoczęciem upewnij się, że zainstalowano i skonfigurowano następujące elementy:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Skonfiguruj maszynę wirtualną uczenia głębokiego Azure

> [!NOTE]
> Ustaw **Typ systemu operacyjnego** na Linux.

Instrukcje dotyczące konfigurowania maszyny wirtualnej do uczenia głębokiego można znaleźć [tutaj](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm).

### <a name="remove-comment-in-parens"></a>Usuń komentarz w parens

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Pobierz przykładowy kod

Pobierz to [repozytorium GitHub](https://github.com/Microsoft/samples-for-ai) zawierające przykłady umożliwiające wprowadzenie do uczenia głębokiego na TENSORFLOW, CNTK, Theano i innych.

## <a name="open-project"></a>Otwieranie projektu

- Uruchom program Visual Studio i wybierz pozycję **plik > otwórz > projektu/rozwiązania**.

- Wybierz folder **przykładów Tensorflow** z pobranego repozytorium Samples i Otwórz plik **TensorflowExamples. sln** .

   ![Otwieranie projektu](media/tensorflow-local/open-project.png)

   ![Otwórz rozwiązanie](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Dodaj zdalną maszynę wirtualną platformy Azure

W Eksplorator serwera kliknij prawym przyciskiem myszy węzeł **maszyny zdalne** w WĘŹLE narzędzia AI i wybierz polecenie "Dodaj...". Wprowadź nazwę wyświetlaną komputera zdalnego, hosta IP, port SSH, nazwę użytkownika i hasło/plik klucza.

![Dodaj nową maszynę zdalną](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Prześlij zadanie do maszyny wirtualnej platformy Azure
Kliknij prawym przyciskiem myszy projekt MNIST ręcznie w obszarze **Eksplorator rozwiązań** i wybierz pozycję **Prześlij zadanie**.

![Przesyłanie zadania do maszyny zdalnej](media/tensorflow-vm/job-submission.png)

W oknie przesyłanie:

- Na liście **klastrów do użycia**wybierz maszynę zdalną (z prefiksem "RM:"), do której chcesz przesłać zadanie.

- Wprowadź **nazwę zadania**.

- Kliknij przycisk **Prześlij**.

## <a name="check-status-of-job"></a>Sprawdź stan zadania
Aby wyświetlić stan i szczegóły zadań: Rozwiń maszynę wirtualną, do której zostało przesłane zadanie, w **Eksplorator serwera**. Kliknij dwukrotnie pozycję **zadania**.

![Przeglądarka zadań](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Czyszczenie zasobów

Zatrzymaj maszynę wirtualną, jeśli planujesz jej używanie w najbliższej przyszłości. Jeśli skończysz korzystać z tego samouczka, uruchom następujące polecenie, aby wyczyścić zasoby:

```azurecli-interactive
az group delete --name myResourceGroup
```
