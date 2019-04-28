---
title: Uruchamianie modelu TensorFlow w chmurze
description: Uruchom modelu tensorflow głębokiego uczenia maszyny wirtualnej platformy Azure
keywords: sztuczna inteligencja, programu visual studio głębokiego uczenia maszyny wirtualnej
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: adb3720f1624f355b99d75bfe446fafab1c5e0ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62427571"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Uczenie modelu TensorFlow w chmurze

W tym samouczku zostanie uczenie modelu TensorFlow przy użyciu [zestawu danych mnist ręcznie ZAPISANYCH](http://yann.lecun.com/exdb/mnist/) na platformie Azure [uczenia głębokiego](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) maszyny wirtualnej.

Bazy danych mnist ręcznie ZAPISANYCH ma zestaw szkolenia 60 000 przykłady i zbiór 10 000 przykłady pisma odręcznego cyfr.

## <a name="prerequisites"></a>Wymagania wstępne
Przed rozpoczęciem upewnij się, że następujące elementy są zainstalowane i skonfigurowane:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Konfigurowanie maszyny wirtualnej do uczenia głębokiego platformy Azure

> [!NOTE]
> Ustaw **typ systemu operacyjnego** z systemem Linux.

Można znaleźć instrukcje dotyczące ustawiania się głębokiego maszyna wirtualna do uczenia [tutaj](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm).

### <a name="remove-comment-in-parens"></a>Usuń komentarz w parens

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Pobierz przykładowy kod

Pobierz ten [repozytorium GitHub](https://github.com/Microsoft/samples-for-ai) zawierający wprowadzenie do uczenia głębokiego na TensorFlow, CNTK, Theano i przykłady.

## <a name="open-project"></a>Otwieranie projektu

- Uruchom program Visual Studio i wybierz **Plik > Otwórz > Projekt/rozwiązanie**.

- Wybierz **przykłady Tensorflow** folderu z repozytorium przykładów pobrany i otwarty **TensorflowExamples.sln** pliku.

   ![Otwieranie projektu](media/tensorflow-local/open-project.png)

   ![Otwórz rozwiązanie](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Dodaj zdalnego maszyny Wirtualnej platformy Azure

Kliknij prawym przyciskiem myszy w Eksploratorze serwera **maszynach zdalnych** węźle węzłem narzędzi sztucznej Inteligencji i wybierz pozycję "Dodaj...". Wprowadź nazwę wyświetlaną maszyny zdalnej, adresu IP hosta, SSH portu, nazwy użytkownika i hasła/klucza pliku.

![Dodaj nowy komputer zdalny](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Prześlij zadanie do maszyny Wirtualnej platformy Azure
Kliknij prawym przyciskiem myszy nad projektem mnist ręcznie ZAPISANYCH w **Eksploratora rozwiązań** i wybierz **Prześlij zadanie**.

![Przesyłanie zadań do maszyny zdalnej](media/tensorflow-vm/job-submission.png)

W oknie przesyłania:

- Na liście **klaster pod kątem używania**, wybierz komputer zdalny (przy użyciu "Menedżera zasobów:" prefiks) można przesłać zadania.

- Wprowadź **Nazwa zadania**.

- Kliknij przycisk **Submit** (Prześlij).

## <a name="check-status-of-job"></a>Sprawdź stan zadania
Aby wyświetlić stan i szczegółowe informacje dotyczące zadań: rozwiń węzeł maszyna wirtualna przesłano zadanie w **Eksploratora serwera**. Kliknij dwukrotnie **zadań**.

![Przeglądarka zadań](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Zatrzymaj maszynę Wirtualną, jeśli planowane jest korzystanie z niej w niedalekiej przyszłości. Po zakończeniu tego samouczka, uruchom następujące polecenie, aby wyczyścić zasoby:

```azurecli-interactive
az group delete --name myResourceGroup
```
