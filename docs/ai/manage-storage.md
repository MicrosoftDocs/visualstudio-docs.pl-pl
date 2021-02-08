---
title: Przeglądaj magazyn, aby przekazać dane
description: Dowiedz się, jak przeglądać wszystkie magazyny na komputerze zdalnym lub udziale plików platformy Azure w celu umożliwienia przekazywania danych lub pobierania modeli i dzienników.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: c32fc5f4ceeb090c8c602b01078fd446249f33eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841422"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Przeglądaj magazyn, aby przekazać dane lub pobrać modele i dzienniki

Możesz przeglądać wszystkie magazyny na komputerze zdalnym lub udziale plików platformy Azure, aby umożliwić przekazywanie danych lub pobieranie modeli i dzienników. Lub, jeśli chcesz uzyskać dostęp do dzienników i danych wyjściowych zadania dla konkretnego zadania, możesz to zrobić również w przeglądarce zadań.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Aby uzyskać dostęp do wszystkich danych na komputerze zdalnym lub udziale plików

1. Otwórz **Eksplorator serwera**.
2. Rozwiń węzeł maszyny zdalnej lub Batch AI kontekstu obliczeniowego.
3. Kliknij prawym przyciskiem myszy pozycję **Magazyn**; następnie kliknij przycisk **Przeglądaj**.

    ![Zrzut ekranu przedstawiający Eksplorator serwera z folderem komputery zdalne rozwinięte. Magazyn jest wyróżniony w drzewie folderów, a w menu kontekstowym wybrano pozycję Przeglądaj.](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Aby uzyskać dostęp do danych specyficznych dla zadania na komputerze zdalnym lub w udziale plików

1. Otwórz [historię zadania](job-details.md)
2. Wybierz zadanie.
3. Kliknij pozycję **folder roboczy** lub kliknij pozycję **stdout/stderr** , aby uzyskać szybki dostęp do tych ważnych plików dziennika.

    ![Zrzut ekranu okna przeglądarki zadań w Eksplorator serwera. Wybrane jest zadanie train_mnist, a w obszarze Szczegóły zadania zostanie wybrane łącze do folderu roboczego.](media/manage-storage/job-workingfolder.png)
