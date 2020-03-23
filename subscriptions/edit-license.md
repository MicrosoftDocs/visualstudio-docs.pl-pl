---
title: Edytowanie subskrypcji w portalu administracyjnym | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Dowiedz się, jak administratorzy mogą edytować przypisania subskrypcji.
ms.openlocfilehash: cd4bb40599ff242e20ba0e38fb561bde7d3f1823
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "78263287"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Edytowanie przydziałów subskrypcji programu Visual Studio
Jako administrator subskrypcji możesz wprowadzać zmiany w subskrypcjach przypisanych do osób w organizacji.  W tym artykule omówiono typy zmian, które można wprowadzić i przedstawiono niezbędne kroki.

   > [!NOTE]
   > Jeśli chcesz zmienić szczegóły subskrypcji dla subskrybenta przypisanego za pośrednictwem grupy usługi Azure Active Directory, należy usunąć je z grupy i dodać je do portalu administracyjnego indywidualnie.  

## <a name="change-subscriber-information"></a>Zmienianie informacji o subskrybentach
Można edytować informacje subskrybenta, aby poprawić błędy lub zaktualizować informacje.

Aby edytować subskrybenta, wybierz elipsy (...) wyświetlane obok adresu e-mail subskrybenta po najechaniu kursorem myszy na niego. Pojawi się listy rozwijanej.  Wybierz **edytuj,** aby zmodyfikować szczegóły subskrybenta. 
> [!div class="mx-imgBorder"]
> ![Wybierz subskrybenta do edycji](_img/edit-license/select-subscriber.png)

Możesz zaktualizować imię, nazwisko subskrybenta, poziom subskrypcji, adres e-mail, kraj, język, pliki do pobrania i pole referencyjne. Edytuj informacje subskrybenta i kliknij przycisk **Zapisz**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Edytowanie wielu subskrybentów przy użyciu edycji zbiorczej
Możesz edytować wielu subskrybentów jednocześnie, korzystając z procesu edycji zbiorczej. Ta funkcja jest używana głównie w przypadku organizacji, które przechodzą zmiany firmowego adresu e-mail lub jeśli organizacja zdecydowała się ograniczyć dostęp do pobierania.

   > [!IMPORTANT]
   > Poziomy subskrypcji (np. enterprise, professional itp.) i identyfikatory GUID subskrypcji nie mogą być zmieniane za pomocą edycji zbiorczej.  Jeśli musisz przypisać określone identyfikatory GUID subskrypcji do użytkowników, użyj procesu dodawania użytkowników, wybierając identyfikator subskrypcji. Jeśli spróbujesz przekazać z tych elementów zmienionych w szablonie edycji zbiorczej, przekazywanie zakończy się niepowodzeniem.

1. Aby edytować wielu subskrybentów jednocześnie, przejdź do karty Subskrybenci. Na wstążce u góry kliknij pozycję **Edycja zbiorcza**.

2. Edycja zbiorcza używa szablonu programu Excel do wprowadzania zmian w informacjach o subskrybentach. W polu Edycja zbiorcza kliknij pozycję **Eksportuj ten program excel,** aby pobrać bieżącą listę subskrybentów wraz ze wszystkimi ich informacjami.
   > [!div class="mx-imgBorder"]
   > ![Edytowanie licencji — eksportowanie zbiorczej listy edycji](_img/edit-license/edit-license-bulk-edit-export.png)

3. Następnie zapisz plik lokalnie, aby można go łatwo znaleźć i wprowadzić niezbędne zmiany przed przesłaniem go. Aby zapewnić pomyślne przekazanie, **nie edytuj poziomu subskrypcji ani identyfikatora GUID subskrypcji** w pliku edycji zbiorczej, ponieważ spowoduje to niepowodzenie przekazywania.

4. Wróć do portalu administracji subskrypcjami programu Visual Studio i w oknie dialogowym Edycja zbiorcza kliknij przycisk **Przeglądaj**. Wybierz zapisany plik programu Excel i kliknij przycisk **OK**. Na ekranie zobaczysz postęp przesyłania.
   > [!div class="mx-imgBorder"]
   > ![Edytowanie licencji — przesyłanie plików edycji zbiorczych](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Po przesłaniu pliku zostanie wyświetlone powiadomienie informujące o jego pomyślnym zakończeniu. W tym momencie zmiany zostaną odzwierciedlone w informacjach o subskrybentach.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Chcesz przypisać określony identyfikator subskrypcji? Zapoznaj się z tworzeniem usługi Przypisywanie identyfikatora subskrypcji. 
- Aby uzyskać pomoc dotyczącą znajdowania określonej subskrypcji, zapoznaj się z [wyszukaj subskrypcję](search-license.md).
- Chcesz utworzyć listę wszystkich subskrypcji?  Sprawdź [eksportuj subskrypcje](exporting-subscriptions.md).


