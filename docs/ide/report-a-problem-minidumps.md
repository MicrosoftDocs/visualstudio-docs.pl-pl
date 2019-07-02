---
title: Tworzenie minizrzutów przy użyciu wszystkich stosy wywołań
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: eefcbefa8b728afa677e7bd04fd538633ae117f0
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518233"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Utwórz minizrzutów dla procesu programu Visual Studio za pomocą wszystkich stosów wywołań

W niektórych przypadkach firmy Microsoft może poprosić o minizrzutu uruchomionego procesu programu Visual Studio z informacjami dla wszystkich stosy wywołań. Do zebrania tych informacji, wykonaj następujące kroki:

## <a name="create-the-minidump-file"></a>Utwórz plik minizrzutu

1. Uruchom nowe wystąpienie programu Visual Studio.
1. W menu głównym wybierz **debugowania** > **dołączanie do procesu**.
1. Sprawdź odpowiedni **zarządzane** i **natywnych** pola wyboru, a następnie naciśnij klawisz **Dołącz**.

   ![Dołącz do procesu](../ide/media/attach-to-process.png)

1. Wybierz inne wystąpienie programu Visual Studio do dołączenia z listy uruchomionych procesów.
1. W menu głównym wybierz **debugowania** > **Przerwij wszystko**.
1. W menu głównym wybierz **debugowania** > **Zapisz zrzut jako**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Uzyskiwanie stosy wywołań minizrzut

1. Otwórz plik zrzutu w programie Visual Studio.

1. Stało się **narzędzia** > **opcje** > **debugowanie** > **symbole** i upewnij się, że  **Serwery symboli firmy Microsoft** jest zaewidencjonowany **symboli (.pdb) lokalizacji**.
1. Otwórz **polecenia** okna (**widoku** > **Windows inne** > **okna polecenia**)
1. Typ ' ~ * k ". W oknie zostaną wyświetlone wszystkie wątki stosy wywołań.
1. Skopiuj cały tekst z okna polecenia i zapisać do pliku tekstowego.
1. Dołączanie plików txt do usterki.
