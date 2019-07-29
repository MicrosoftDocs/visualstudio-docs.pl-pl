---
title: Przypisywanie licencji do grup użytkowników dla subskrypcji programu Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą przypisywać licencje do wielu subskrybentów
ms.openlocfilehash: 7d54dcf3cf3e7fea7845a4e9a0053de4ba734ae9
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68611905"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Przypisywanie subskrypcji wielu użytkownikom
Portal administrowania subskrypcjami pozwala dodawać użytkowników jeden w czasie lub w dużych grupach.  Aby dodać poszczególnych użytkowników, zobacz [Dodawanie pojedynczych użytkowników](assign-license.md).

## <a name="use-bulk-add-to-assign-subscriptions"></a>Używanie dodatków zbiorczych do przypisywania subskrypcji
1. Zaloguj się do portalu administracyjnego subskrypcji programu Visual Studio pod https://manage.visualstudio.com adresem.
2. Aby jednocześnie dodać wielu subskrybentów, przejdź do karty **Zarządzanie subskrybentami** . Na Wstążce u góry kliknij pozycję **Dodaj zbiorczo**.
   > [!div class="mx-imgBorder"]
   > ![Dodawanie wielu subskrybentów](media/add-multiple-subscribers.png)

2. Dodawanie zbiorcze używa szablonu programu Microsoft Excel do przekazywania informacji o subskrybencie. W oknie dialogowym przekazywanie wielu subskrybentów kliknij pozycję **Pobierz** , aby pobrać szablon.
   > [!div class="mx-imgBorder"]
   > ![Pobierz szablon programu Excel, aby przekazać wielu subskrybentów](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Zawsze Pobieraj najnowszą wersję tego szablonu. Jeśli używasz starszej wersji, przekazywanie zbiorcze może zakończyć się niepowodzeniem.

3. W arkuszu kalkulacyjnym programu Excel Wypełnij pola informacjami dla osób, do których chcesz przypisać subskrypcje. (*Odwołanie* jest polem opcjonalnym). Zapisz plik lokalnie po zakończeniu.

   Aby zapewnić bezproblemowe przekazywanie, należy przestrzegać następujących najlepszych rozwiązań:

    - Upewnij się, że żadne z pól formularza nie zawiera przecinków.
    - Usuń odstępy przed i po polach formularza.
    - Upewnij się, że nazwy użytkowników nie zawierają dodatkowych spacji między imioną lub nazwiskiem dwóch części (na przykład jeśli osoba ma dwuczęściową nazwę, taką jak "Maggie", należy ją wpisać jako "MaggieMay", ponieważ system nie przycinania dodatkowego miejsca).

4. Wróć do portalu administracyjnego subskrypcji programu Visual Studio. W oknie dialogowym **przekazywanie wielu subskrybentów** kliknij przycisk **Przeglądaj**.
   > [!div class="mx-imgBorder"]
   > ![Przejdź do zapisanego szablonu, aby przekazać wielu subskrybentów](media/bulk-add-browse-saved-template.png)

5. Przejdź do zapisanego pliku programu Excel, a następnie kliknij przycisk **OK**.
   > [!div class="mx-imgBorder"]
   > ![Przekaż szablon programu Excel, aby przekazać wielu subskrybentów](media/bulk-upload-subscribers.png)

    Zostanie wyświetlone okno dialogowe postęp przekazywania.

    Jeśli szablon zawiera błędy, przekazywanie zakończy się niepowodzeniem, a błędy zostaną wyświetlone, aby można było poprawić szablon i ponowić próbę przekazania zbiorczego.
   > [!div class="mx-imgBorder"]
   > ![Komunikat o błędzie, jeśli przekazywanie wielu subskrybentów zakończy się niepowodzeniem](media/bulk-add-template-failed.png)

    Po pomyślnym przekazaniu zostanie wyświetlona lista subskrybentów i komunikat z potwierdzeniem.
   > [!div class="mx-imgBorder"]
   > ![Komunikat z potwierdzeniem, jeśli przekazywanie wielu subskrybentów powiedzie się](media/bulk-add-template-success.png)

## <a name="next-steps"></a>Następne kroki
- Masz tylko jednego lub dwóch subskrybentów do dodania?  Wyewidencjonowywanie [dodawania pojedynczych użytkowników](assign-license.md)
- Dowiedz się, jak [edytować](edit-license.md) istniejące subskrypcje
- Czy potrzebujesz pomocy? Skontaktuj się z [pomocą techniczną programu Visual Studio Administration i subscriptions](https://visualstudio.microsoft.com/support/support-overview-vs).
