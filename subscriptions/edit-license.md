---
title: Edytuj subskrypcje w portalu administracyjnym | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą edytować przypisania subskrypcji.
ms.openlocfilehash: e55cee74f861973e3cc29e3f19dc9b31a107f437
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605664"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Edytuj przypisania subskrypcji programu Visual Studio
Administrator subskrypcji może wprowadzać zmiany w subskrypcjach przypisanych do osób w organizacji.  W tym artykule omówiono typy zmian, które można wprowadzić, i przedstawiono niezbędne kroki.

## <a name="change-subscriber-information"></a>Zmień informacje o subskrybencie
Można edytować informacje o subskrybencie w celu poprawienia błędów lub aktualizacji informacji.

Aby edytować abonenta, wybierz wielokropek (...), który pojawia się obok adresu e-mail subskrybenta po umieszczeniu nad nim wskaźnika myszy. Zostanie wyświetlona lista rozwijana.  Wybierz pozycję **Edytuj** , aby zmodyfikować szczegóły subskrybenta. Możesz również kliknąć dwukrotnie wiersz subskrybenta w siatce, aby otworzyć okno Edycja.
> [!div class="mx-imgBorder"]
> ![Wybierz subskrybenta do edycji](_img/edit-license/select-subscriber.png)

Możesz zaktualizować imię, nazwisko, kraj, język i pliki do pobrania. Edytuj informacje o subskrybencie, a następnie kliknij przycisk **Zapisz**.

   > [!NOTE]
   > Jeśli musisz zmienić poziom subskrypcji dla subskrybenta, musisz usunąć użytkownika z portalu i dodać go ponownie. Nie można edytować poziomów subskrypcji.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Edytowanie wielu subskrybentów przy użyciu edycji zbiorczej
Jednocześnie można edytować wielu subskrybentów przy użyciu procesu edycji zbiorczej. Ta funkcja jest używana głównie w przypadku organizacji, które przechodzą przez firmowe adresy e-mail, lub jeśli organizacja zdecydowała się ograniczyć dostęp do plików do pobrania.

   > [!IMPORTANT]
   > Nie można zmienić poziomów subskrypcji (tj. Enterprise, Professional itp.) ani identyfikatorów GUID subskrypcji.  W przypadku próby przekazania tych elementów zmieniono przekazywanie nie powiedzie się.

1. Aby jednocześnie edytować wielu subskrybentów, przejdź do karty Subskrybenci. Na Wstążce u góry kliknij pozycję **Edytuj zbiorczo**.

2. Edycja zbiorcza używa szablonu programu Excel do wprowadzania zmian w informacjach o subskrybencie. W polu edycji zbiorczej kliknij pozycję **Eksportuj ten program Excel** , aby pobrać bieżącą listę subskrybentów, w tym wszystkie informacje.
   > [!div class="mx-imgBorder"]
   > ![Edycja licencji-eksportowanie list edycji zbiorczej](_img/edit-license/edit-license-bulk-edit-export.png)

3. Następnie Zapisz plik lokalnie, aby można było go łatwo znaleźć i wprowadzić wszelkie niezbędne zmiany przed jego przekazaniem. Aby zapewnić pomyślne przekazywanie, **nie należy edytować poziomu subskrypcji lub identyfikatora GUID subskrypcji** w taki sposób, aby przekazywanie nie powiodło się.

4. Wróć do portalu administracyjnego subskrypcji programu Visual Studio i w oknie dialogowym Edycja zbiorcza kliknij przycisk **Przeglądaj**. Wybierz zapisany plik programu Excel, a następnie kliknij przycisk **OK**. Postęp przekazywania zostanie wyświetlony na ekranie.
   > [!div class="mx-imgBorder"]
   > ![Edytowanie licencji — przekazywanie plików edycji zbiorczej](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Po przesłaniu pliku zobaczysz powiadomienie informujące o pomyślnym zapoznaniu się z nim. W tym momencie zmiany zostaną odzwierciedlone w informacjach o subskrybencie.

## <a name="next-steps"></a>Następne kroki
- Aby uzyskać pomoc dotyczącą znajdowania określonej subskrypcji, zapoznaj się z tematem [Wyszukiwanie w ramach subskrypcji](search-license.md).
- Chcesz utworzyć listę wszystkich Twoich subskrypcji?  Sprawdź [subskrypcje eksportowania](exporting-subscriptions.md).