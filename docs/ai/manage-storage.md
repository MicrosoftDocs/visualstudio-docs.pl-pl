---
title: Przeglądaj magazyn, aby przekazać dane
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 188ebee353261ba49f6677a0f96db68b7e8d46d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371615"
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
