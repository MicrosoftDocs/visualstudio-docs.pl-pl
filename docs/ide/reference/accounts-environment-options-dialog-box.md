---
title: Informacje o opcjach kont
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63b5443599e5e84cab1693aca4281c882c082162
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645336"
---
# <a name="accounts-environment-options-dialog-box"></a>Konta, środowisko, Opcje — okno dialogowe

Ta strona służy do ustawiania różnych opcji związanych z kontami używanymi do logowania się w programie Visual Studio.

## <a name="personalization-account"></a>Konto personalizacji

### <a name="synchronize-settings-across-devices"></a>Synchronizuj ustawienia między urządzeniami

Użyj tej opcji, aby określić, czy synchronizować ustawienia na wielu maszynach. Aby uzyskać więcej informacji, zobacz [Ustawienia zsynchronizowane](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Włącz przepływ kodu urządzenia

Po wybraniu tej opcji zachowanie programu Visual Studio zmienia się, gdy wybierzesz pozycję **Dodaj konto** na stronie**ustawień konta**  >  **pliku** . Zamiast wyświetlania strony **logowania do konta** zostanie wyświetlone okno dialogowe z adresem URL i kodem do wklejenia do przeglądarki sieci Web w celu zalogowania się. Ta opcja jest przydatna w przypadkach, gdy nie można zalogować się do programu Visual Studio w zwykły sposób, na przykład jeśli używasz starszej wersji programu Internet Explorer lub Zapora ogranicza dostęp. Aby uzyskać więcej informacji, zobacz [pracy z wieloma kontami użytkowników](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Zarejestrowane chmury platformy Azure

W tej sekcji przedstawiono wystąpienia chmury platformy Azure, do których masz dostęp, za pomocą co najmniej jednego konta używanego do logowania się w programie Visual Studio. Na przykład możesz mieć dostęp do prywatnego wystąpienia platformy Azure w centrum danych firmy. Możesz też mieć dostęp do suwerennego lub rządowego wystąpienia platformy Azure, takiego jak Azure Chiny 21 Vianet lub administracja Stanów Zjednoczonych na platformie Azure. Globalne wystąpienie chmury platformy Azure zostanie wyświetlone na liście domyślnie i nie można go usunąć.

Zarejestruj dodatkową chmurę platformy Azure, wybierając przycisk **Dodaj** . W oknie dialogowym **Dodawanie nowej chmury platformy Azure** wyświetlane są kilka dobrze znanych wystąpień w chmurze platformy Azure, z którymi można nawiązać połączenie, lub możesz wprowadzić adres URL do prywatnego punktu końcowego platformy Azure.

![Dodaj nowe wystąpienie chmury platformy Azure](media/add-new-azure-cloud.png)

Po zarejestrowaniu dodatkowej chmury platformy Azure Możesz wybrać chmurę platformy Azure, do której chcesz się zalogować po zalogowaniu się do programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- [Synchronizowanie ustawień na wielu komputerach](../synchronized-settings-in-visual-studio.md)
- [Logowanie do programu Visual Studio](../signing-in-to-visual-studio.md)
- [Praca z wieloma kontami użytkowników](../work-with-multiple-user-accounts.md)
- [Ustawienia środowiska](../environment-settings.md)