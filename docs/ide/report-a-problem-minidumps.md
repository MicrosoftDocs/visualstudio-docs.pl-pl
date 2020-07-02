---
title: Utwórz minizrzutów ze wszystkimi stosami wywołań
ms.date: 06/27/2019
ms.topic: how-to
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
ms.openlocfilehash: 8af2ef642a1c2422d470c716e14dca7d2e0168eb
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770835"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Utwórz minizrzutów dla procesu programu Visual Studio ze wszystkimi stosami wywołań

W niektórych przypadkach firma Microsoft może zażądać minizrzutu uruchomionego procesu programu Visual Studio z informacjami dla wszystkich stosów wywołań. Aby zebrać te informacje, wykonaj następujące kroki:

## <a name="create-the-minidump-file"></a>Utwórz plik minizrzutu

1. Uruchom nowe wystąpienie programu Visual Studio.
1. Z menu głównego wybierz polecenie **Debuguj**  >  **Dołącz do procesu**.
1. Zaznacz odpowiednie pola wyboru **zarządzane** i **natywne** i naciśnij przycisk **Dołącz**.

   ![Dołącz do procesu](../ide/media/attach-to-process.png)

1. Wybierz inne wystąpienie programu Visual Studio do dołączenia z listy uruchomionych procesów.
1. Z menu głównego wybierz kolejno opcje **Debuguj**  >  **Przerwij wszystko**.
1. Z menu głównego wybierz **Debuguj**  >  **Zapisz zrzut jako**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Pobierz stosy wywołań z minizrzutu

1. Otwórz plik zrzutu w programie Visual Studio.
1. Przejdź do **Tools**  >  **opcji Narzędzia Opcje**  >  **debugowania**  >  **symbole** i upewnij się, że **serwery symboli firmy Microsoft** są zaznaczone w **lokalizacji pliku symboli (. pdb)**.
1. Otwórz okno **wiersza polecenia** (**Wyświetl**  >  **inne**  >  **okno polecenia**systemu Windows)
1. Typ "~ * k". W oknie zostaną wyświetlone stosy wywołań wszystkich wątków.
1. Skopiuj cały tekst z okna poleceń i Zapisz go w pliku tekstowym.
1. Dołącz plik txt do usterki.
