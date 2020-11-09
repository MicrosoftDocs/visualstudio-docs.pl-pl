---
title: Edytuj subskrypcje programu Visual Studio w portalu administracyjnym | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 11/09/2020
ms.topic: how-to
description: Dowiedz się, jak Administratorzy mogą edytować przypisania subskrypcji.
ms.openlocfilehash: 785bad481e4329647582d1f441988b1cd83a055a
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382497"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Edytuj przypisania subskrypcji programu Visual Studio
Administrator subskrypcji może wprowadzać zmiany w subskrypcjach przypisanych do osób w organizacji.  W tym artykule omówiono typy zmian, które można wprowadzić, i przedstawiono niezbędne kroki.

   > [!NOTE]
   > Aby zmienić szczegóły subskrypcji dla subskrybenta przypisanego za pośrednictwem grupy Azure Active Directory, należy usunąć je z grupy i dodać je do portalu administracyjnego osobno.  

## <a name="change-subscriber-information"></a>Zmień informacje o subskrybencie
Można edytować informacje o subskrybencie w celu poprawienia błędów lub aktualizacji informacji.

Aby edytować abonenta, wybierz wielokropek (...), który pojawia się obok adresu e-mail subskrybenta po umieszczeniu nad nim wskaźnika myszy. Zostanie wyświetlona lista rozwijana.  Wybierz pozycję **Edytuj** , aby zmodyfikować szczegóły subskrybenta. 
> [!div class="mx-imgBorder"]
> ![Wybierz subskrybenta do edycji](_img/edit-license/select-subscriber.png "Kliknij wielokropek i wybierz polecenie Edytuj.")

Możesz zaktualizować imię i nazwisko subskrybenta, nazwisko, poziom subskrypcji, adres e-mail, kraj, język, pobrania i pole odwołania. Edytuj informacje o subskrybencie i kliknij przycisk **Zapisz**.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Edytowanie wielu subskrybentów przy użyciu edycji zbiorczej


Jednocześnie można edytować wielu subskrybentów przy użyciu procesu edycji zbiorczej. Ta funkcja jest używana głównie w przypadku organizacji, które przechodzą przez firmowe adresy e-mail, lub jeśli organizacja zdecydowała się ograniczyć dostęp do plików do pobrania.

Obejrzyj ten film wideo lub przeczytaj, aby dowiedzieć się, jak edytować wielu subskrybentów za pomocą edycji zbiorczej. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]


1. Aby jednocześnie edytować wielu subskrybentów, przejdź do karty Subskrybenci. Na Wstążce u góry kliknij pozycję **Edytuj zbiorczo**.

2. Edycja zbiorcza używa szablonu programu Excel do wprowadzania zmian w informacjach o subskrybencie. W polu edycji zbiorczej kliknij pozycję **Eksportuj ten program Excel** , aby pobrać bieżącą listę subskrybentów, w tym wszystkie informacje.
   > [!div class="mx-imgBorder"]
   > ![Edycja licencji-eksportowanie list edycji zbiorczej](_img/edit-license/edit-license-bulk-edit-export.png "Kliknij pozycję Eksportuj ten program Excel, aby utworzyć listę bieżących subskrypcji.")

3. Następnie Zapisz plik lokalnie, aby można było go łatwo znaleźć i wprowadzić wszelkie niezbędne zmiany przed jego przekazaniem. Aby zapewnić pomyślne przekazywanie, **nie należy edytować poziomu subskrypcji lub identyfikatora GUID subskrypcji** w pliku edycji zbiorczej w taki sposób, że spowoduje to niepowodzenie przekazywania.

4. Wróć do portalu administracyjnego subskrypcji programu Visual Studio i w oknie dialogowym Edycja zbiorcza kliknij przycisk **Przeglądaj**. Wybierz zapisany plik programu Excel, a następnie kliknij przycisk **OK**. Postęp przekazywania zostanie wyświetlony na ekranie.
   > [!div class="mx-imgBorder"]
   > ![Edytowanie licencji — przekazywanie plików edycji zbiorczej](_img/edit-license/edit-license-bulk-file-upload1.png "Przejdź do lokalizacji ukończonego pliku programu Excel, wybierz go, a następnie kliknij przycisk OK.")

5. Po przesłaniu pliku zobaczysz powiadomienie informujące o pomyślnym zapoznaniu się z nim. W tym momencie zmiany zostaną odzwierciedlone w informacjach o subskrybencie.

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Chcesz przypisać określony identyfikator subskrypcji? Sprawdź przypisanie identyfikatora subskrypcji. 
- Aby uzyskać pomoc dotyczącą znajdowania określonej subskrypcji, zapoznaj się z tematem [Wyszukiwanie w ramach subskrypcji](search-license.md).
- Chcesz utworzyć listę wszystkich Twoich subskrypcji?  Sprawdź [subskrypcje eksportowania](exporting-subscriptions.md).