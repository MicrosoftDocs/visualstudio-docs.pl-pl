---
title: Edytować subskrypcje w portalu administratora | Dokumentacja firmy Microsoft
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: conceptual
description: Dowiedz się, jak Administratorzy mogą edytować przypisania subskrypcji.
searchscope: VS Subscription
ms.openlocfilehash: d3dbc2e05d85ed8277d7a7c0f530dfa92da7dba6
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840539"
---
# <a name="editing-visual-studio-subscription-assignments"></a>Edytowanie przypisania subskrypcji programu Visual Studio

Jako administratora subskrypcji programu użytkownik wprowadzać zmiany do subskrypcji, przypisane do osoby w Twojej organizacji.  W tym artykule omówiono rodzaje zmian, może być i zawiera niezbędne instrukcje.

## <a name="making-changes-to-subscriber-information"></a>Wprowadzanie zmian do subskrybenta informacji
Można edytować informacje o subskrybenta, aby poprawić błędy lub zaktualizować informacje.

Aby edytować subskrybenta, wybierz wielokropek (...), które pojawiają się obok adres e-mail subskrybenta, po umieszczeniu wskaźnika myszy nad nim. Pojawi się listy rozwijanej.  Wybierz **Edytuj** Aby zmodyfikować szczegóły subskrybenta. Możesz także dwukrotnie kliknąć na subskrybenta wierszy w siatce, aby otworzyć okno edycji.
> [!div class="mx-imgBorder"]
> ![Wybierz subskrybenta do edycji](_img/edit-license/select-subscriber.png)

Możesz zaktualizować imię, nazwisko subskrybenta, kraj, język i pliki do pobrania. Edytuj informacje na subskrybenta, a następnie kliknij przycisk **Zapisz**.

   > [!NOTE]
   > Jeśli potrzebujesz zmienić poziom subskrypcji dla subskrybenta, należy usunąć użytkownika z portalu i dodać je ponownie. Poziomy subskrypcji jest niemożliwa.

## <a name="editing-multiple-subscribers-using-bulk-edit"></a>Edycja wielu subskrybentów przy użyciu Edycja zbiorcza

Możesz edytować wielu subskrybentów jednocześnie przy użyciu procesu edycji zbiorczej. Ta funkcja jest głównie używana w organizacjach, które są przesyłane za pośrednictwem firmowych wiadomości e-mail zmiany adresu lub jeśli podjęto decyzję o ograniczanie dostępu do plików do pobrania dla organizacji.

   > [!IMPORTANT]
   > Subskrypcja poziomy (tj. Enterprise, Professional, itp.) i identyfikatorów GUID subskrypcji nie może być zmieniona.  Jeśli spróbujesz przekazać pliki z następującymi elementami zmienione przekazywanie zakończy się niepowodzeniem.

1. Aby edytować wielu subskrybentów jednocześnie, przejdź do karty subskrybentów. Na Wstążce u góry kliknij **zbiorczo edytować**.

2. Edycja zbiorcza korzysta z szablonu programu Excel, należy edytować informacje abonenta. W polu edycji zbiorczej kliknij **eksportu ten skoroszyt programu excel** można pobrać bieżącą listę subskrybentów wraz ze wszystkimi informacjami.
   > [!div class="mx-imgBorder"]
   > ![Edytowanie eksportu licencję — lista Edycja zbiorcza](_img/edit-license/edit-license-bulk-edit-export.png)

3. Następnie należy zapisać plik lokalnie, można łatwo znaleźć go i wprowadź niezbędne zmiany przed ich przekazaniem. Do zapewnienia pomyślnego wysłania **nie należy ich edytować poziomie subskrypcji lub identyfikator GUID subskrypcji** jako spowodowałoby przekazywania nie powiedzie się.

4. Wróć do portalu administratora subskrypcji programu Visual Studio i w oknie dialogowym Edycja zbiorcza, kliknij przycisk **Przeglądaj**. Wybierz plik programu Excel został zapisany, a następnie kliknij przycisk **OK**. Postęp przekazywania zobaczą na ekranie.
   > [!div class="mx-imgBorder"]
   > ![Edytowanie licencję — przekazywanie pliku Edycja zbiorcza](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Po przekazaniu pliku, zobaczysz powiadomienie z informacją o tym, że było pomyślne. W tym momencie zmiany zostaną odzwierciedlone w informacji dotyczących subskrybenta.
