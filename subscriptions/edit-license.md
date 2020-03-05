---
title: Edytuj subskrypcje w portalu administracyjnym | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą edytować przypisania subskrypcji.
ms.openlocfilehash: cd4bb40599ff242e20ba0e38fb561bde7d3f1823
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263287"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Edytuj przypisania subskrypcji programu Visual Studio
Administrator subskrypcji może wprowadzać zmiany w subskrypcjach przypisanych do osób w organizacji.  W tym artykule omówiono typy zmian, które można wprowadzić, i przedstawiono niezbędne kroki.

   > [!NOTE]
   > Aby zmienić szczegóły subskrypcji dla subskrybenta przypisanego za pośrednictwem grupy Azure Active Directory, należy usunąć je z grupy i dodać je do portalu administracyjnego osobno.  

## <a name="change-subscriber-information"></a>Zmień informacje o subskrybencie
Można edytować informacje o subskrybencie w celu poprawienia błędów lub aktualizacji informacji.

Aby edytować abonenta, wybierz wielokropek (...), który pojawia się obok adresu e-mail subskrybenta po umieszczeniu nad nim wskaźnika myszy. Zostanie wyświetlona lista rozwijana.  Wybierz pozycję **Edytuj** , aby zmodyfikować szczegóły subskrybenta. 
> [!div class="mx-imgBorder"]
> ![wybierz subskrybenta do edycji](_img/edit-license/select-subscriber.png)

Możesz zaktualizować imię i nazwisko subskrybenta, nazwisko, poziom subskrypcji, adres e-mail, kraj, język, pobrania i pole odwołania. Edytuj informacje o subskrybencie i kliknij przycisk **Zapisz**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Edytowanie wielu subskrybentów przy użyciu edycji zbiorczej
Jednocześnie można edytować wielu subskrybentów przy użyciu procesu edycji zbiorczej. Ta funkcja jest używana głównie w przypadku organizacji, które przechodzą przez firmowe adresy e-mail, lub jeśli organizacja zdecydowała się ograniczyć dostęp do plików do pobrania.

   > [!IMPORTANT]
   > Poziomów subskrypcji (tj. Enterprise, Professional itp.) i identyfikatorów GUID subskrypcji nie można zmienić za pomocą edycji zbiorczej.  Jeśli musisz przypisać określonych identyfikatorów GUID subskrypcji użytkownikom, Użyj procesu dodawania użytkowników, wybierając identyfikator subskrypcji. Jeśli próba przekazania z tymi elementami została zmieniona w szablonie edycji zbiorczej, przekazywanie zakończy się niepowodzeniem.

1. Aby jednocześnie edytować wielu subskrybentów, przejdź do karty Subskrybenci. Na Wstążce u góry kliknij pozycję **Edytuj zbiorczo**.

2. Edycja zbiorcza używa szablonu programu Excel do wprowadzania zmian w informacjach o subskrybencie. W polu edycji zbiorczej kliknij pozycję **Eksportuj ten program Excel** , aby pobrać bieżącą listę subskrybentów, w tym wszystkie informacje.
   > [!div class="mx-imgBorder"]
   > ![edytowania list licencji-eksportowanie zmian zbiorczych](_img/edit-license/edit-license-bulk-edit-export.png)

3. Następnie Zapisz plik lokalnie, aby można było go łatwo znaleźć i wprowadzić wszelkie niezbędne zmiany przed jego przekazaniem. Aby zapewnić pomyślne przekazywanie, **nie należy edytować poziomu subskrypcji lub identyfikatora GUID subskrypcji** w pliku edycji zbiorczej w taki sposób, że spowoduje to niepowodzenie przekazywania.

4. Wróć do portalu administracyjnego subskrypcji programu Visual Studio i w oknie dialogowym Edycja zbiorcza kliknij przycisk **Przeglądaj**. Wybierz zapisany plik programu Excel, a następnie kliknij przycisk **OK**. Postęp przekazywania zostanie wyświetlony na ekranie.
   > [!div class="mx-imgBorder"]
   > ![edytujących](_img/edit-license/edit-license-bulk-file-upload1.png) przekazywaniem plików edycji licencji zbiorczej

5. Po przesłaniu pliku zobaczysz powiadomienie informujące o pomyślnym zapoznaniu się z nim. W tym momencie zmiany zostaną odzwierciedlone w informacjach o subskrybencie.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Chcesz przypisać określony identyfikator subskrypcji? Sprawdź przypisanie identyfikatora subskrypcji. 
- Aby uzyskać pomoc dotyczącą znajdowania określonej subskrypcji, zapoznaj się z tematem [Wyszukiwanie w ramach subskrypcji](search-license.md).
- Chcesz utworzyć listę wszystkich Twoich subskrypcji?  Sprawdź [subskrypcje eksportowania](exporting-subscriptions.md).


