---
title: Tworzenie minidumps ze wszystkimi stosami połączeń
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7b3be91e5d0d2e1f14724dd647670fc4885bcd4d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271189"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Tworzenie minidumps dla procesu visual studio ze wszystkimi stosami wywołań

W niektórych przypadkach firma Microsoft może poprosić o minidump uruchomionego procesu programu Visual Studio z informacjami dla wszystkich stosów wywołań. Aby zebrać te informacje, wykonaj następujące czynności:

## <a name="create-the-minidump-file"></a>Tworzenie pliku minidump

1. Uruchom nowe wystąpienie programu Visual Studio.
1. Z menu głównego wybierz polecenie **Debug** > **attach to process**.
1. Zaznacz odpowiednie pole wyboru **Zarządzane** i **natywne** i naciśnij **przycisk Dołącz**.

   ![Dołącz do procesu](../ide/media/attach-to-process.png)

1. Wybierz inne wystąpienie programu Visual Studio, do które chcesz dołączyć, z listy uruchomionych procesów.
1. Z menu głównego wybierz **polecenie Debug** > **Break All**.
1. Z menu głównego wybierz polecenie **Debug** > **Save Dump As**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Pobierz stosy połączeń z minidump

1. Otwórz plik zrzutu w programie Visual Studio.
1. Przejdź do pozycji**Opcje** >  **narzędzi** > **Debugowanie** > **symboli** i upewnij się, że **serwery symboli firmy Microsoft** są sprawdzane w **lokalizacjach pliku symbolu (pdb).**
1. Otwieranie okna **polecenia** **(Wyświetlanie** > **okna polecenia systemu Windows** > **Command Window**)
1. Wpisz "~*k". W oknie są wyświetlane stosy wywołań wszystkich wątków.
1. Skopiuj cały tekst z okna polecenia i zapisz go w pliku tekstowym.
1. Dołącz plik txt do błędu.
