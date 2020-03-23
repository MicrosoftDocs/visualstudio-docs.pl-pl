---
title: Uruchamianie modelu TensorFlow w chmurze
description: uruchamianie modelu tensorflow w usłudze Azure Deep Learning vm
keywords: ai, studio wizualne, maszyna wirtualna uczenia głębokiego
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 9cb06220c99abb86c24808f6831cf98280133f2e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75915826"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Trenuj model TensorFlow w chmurze

W tym samouczku będziemy szkolić model TensorFlow przy użyciu [zestawu danych MNIST](http://yann.lecun.com/exdb/mnist/) na maszynie wirtualnej usługi Azure [Deep Learning.](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)

Baza danych MNIST ma zestaw szkoleniowy 60 000 przykładów i zestaw testów zawierający 10 000 przykładów cyfr odręcznych.

## <a name="prerequisites"></a>Wymagania wstępne
Przed rozpoczęciem upewnij się, że masz zainstalowane i skonfigurowane następujące elementy:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Konfigurowanie maszyny wirtualnej usługi Azure Deep Learning

> [!NOTE]
> Ustaw **typ systemu operacyjnego** na Linuksa.

Instrukcje dotyczące konfigurowania maszyny wirtualnej uczenia głębokiego można znaleźć [tutaj](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm).

### <a name="remove-comment-in-parens"></a>Usuwanie komentarza w parens

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Pobierz przykładowy kod

Pobierz to [repozytorium GitHub](https://github.com/Microsoft/samples-for-ai) zawierające przykłady, aby rozpocząć naukę głębinową na TensorFlow, CNTK, Theano i innych.

## <a name="open-project"></a>Otwieranie projektu

- Uruchom program Visual Studio i wybierz **opcję > otwórz > projekt/rozwiązanie**.

- Wybierz folder **Tensorflow Examples** z pobranego repozytorium próbek i otwórz plik **TensorflowExamples.sln.**

   ![Otwieranie projektu](media/tensorflow-local/open-project.png)

   ![Otwarte rozwiązanie](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Dodawanie zdalnej maszyny Wirtualnej platformy Azure

W Eksploratorze serwera kliknij prawym przyciskiem myszy węzeł **Maszyny zdalne** w węźle Narzędzia AI i wybierz "Dodaj...". Wprowadź nazwę wyświetlaną komputera zdalnego, hosta IP, portu SSH, nazwę użytkownika i plik hasła/klucza.

![Dodawanie nowego komputera zdalnego](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Przesyłanie zadania do maszyny Wirtualnej platformy Azure
Kliknij prawym przyciskiem myszy projekt MNIST w **Eksploratorze rozwiązań** i wybierz pozycję **Prześlij zadanie**.

![Przesyłanie zadań do komputera zdalnego](media/tensorflow-vm/job-submission.png)

W oknie przesyłania:

- Na liście **Cluster do użycia**wybierz komputer zdalny (z prefiksem "rm:"), do którego ma zostać przesłane zadanie.

- Wprowadź **nazwę zadania**.

- Kliknij **przycisk Prześlij**.

## <a name="check-status-of-job"></a>Sprawdź stan zadania
Aby wyświetlić stan i szczegóły zadań: rozwiń maszynę wirtualną, do której przesłano zadanie w **Eksploratorze serwera**. Kliknij dwukrotnie **jobs**.

![Przeglądarka zadań](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Zatrzymaj maszynę wirtualną, jeśli planujesz używać jej w najbliższej przyszłości. Jeśli zakończenie pracy z tym samouczkiem, uruchom następujące polecenie, aby oczyścić swoje zasoby:

```azurecli-interactive
az group delete --name myResourceGroup
```
