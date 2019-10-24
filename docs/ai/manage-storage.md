---
title: Przeglądaj magazyn, aby przekazać dane
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 7d0f2522117f4c5a5b85e99e2779d10cffcb7f22
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777409"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Przeglądaj magazyn, aby przekazać dane lub pobrać modele i dzienniki

Możesz przeglądać wszystkie magazyny na komputerze zdalnym lub udziale plików platformy Azure, aby umożliwić przekazywanie danych lub pobieranie modeli i dzienników. Lub, jeśli chcesz uzyskać dostęp do dzienników i danych wyjściowych zadania dla konkretnego zadania, możesz to zrobić również w przeglądarce zadań.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Aby uzyskać dostęp do wszystkich danych na komputerze zdalnym lub udziale plików

1. Otwórz **Eksplorator serwera**.
2. Rozwiń węzeł maszyny zdalnej lub Batch AI kontekstu obliczeniowego.
3. Kliknij prawym przyciskiem myszy pozycję **Magazyn**; następnie kliknij przycisk **Przeglądaj**.

    ![magazyn](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Aby uzyskać dostęp do danych specyficznych dla zadania na komputerze zdalnym lub w udziale plików

1. Otwórz [historię zadania](job-details.md)
2. Wybierz zadanie.
3. Kliknij pozycję **folder roboczy** lub kliknij pozycję **stdout/stderr** , aby uzyskać szybki dostęp do tych ważnych plików dziennika.

    ![magazyn](media/manage-storage/job-workingfolder.png)
