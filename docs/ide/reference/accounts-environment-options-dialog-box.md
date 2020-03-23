---
title: Odwołanie do opcji kont
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff457523024db49502ae982a390d9a7be6ba9dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595907"
---
# <a name="accounts-environment-options-dialog-box"></a>Okno dialogowe Konta, Środowisko, Opcje

Ta strona służy do ustawiania różnych opcji związanych z kontami używanymi do logowania się do programu Visual Studio.

## <a name="personalization-account"></a>Konto personalizacji

### <a name="synchronize-settings-across-devices"></a>Synchronizowanie ustawień na różnych urządzeniach

Ta opcja służy do określania, czy ustawienia mają być synchronizowane na wielu komputerach. Aby uzyskać więcej informacji, zobacz [Ustawienia zsynchronizowane](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Włączanie przepływu kodu urządzenia

Po wybraniu tej opcji zachowanie programu Visual Studio zmienia się po **wybraniu** opcji Dodaj konto na stronie**Ustawienia konta** **plików.** >  Zamiast widzieć stronę **Logowania się na koncie,** zostanie wyświetlone okno dialogowe z adresem URL i kodem do wklejenia do przeglądarki internetowej w celu zalogowania się. Ta opcja jest przydatna w przypadkach, gdy nie można zalogować się do programu Visual Studio w zwykły sposób, na przykład, jeśli używasz starszej wersji programu Internet Explorer lub jeśli zapora ogranicza dostęp. Aby uzyskać więcej informacji, zobacz [Praca z wieloma kontami użytkowników](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Zarejestrowane chmury platformy Azure

W tej sekcji przedstawiono wystąpienia chmury platformy Azure, do których masz dostęp za pośrednictwem co najmniej jednego konta używanego do logowania się do programu Visual Studio. Na przykład możesz mieć dostęp do prywatnego wystąpienia platformy Azure w centrum danych twojej firmy. Możesz też mieć dostęp do suwerennego lub rządowego wystąpienia platformy Azure, takiego jak Azure China 21 Vianet lub Azure U.S. Government. Globalne wystąpienie chmury platformy Azure pojawia się domyślnie na liście i nie można go usunąć.

Zarejestruj dodatkową chmurę platformy Azure, wybierając przycisk **Dodaj.** Okno dialogowe **Dodaj nową usługę Azure Cloud** zawiera listę kilku dobrze znanych wystąpień chmury platformy Azure, z którymi można się połączyć, lub można wprowadzić adres URL do prywatnego punktu końcowego platformy Azure.

![Dodawanie nowego wystąpienia chmury platformy Azure](media/add-new-azure-cloud.png)

Po zarejestrowaniu dodatkowej chmury platformy Azure możesz wybrać chmurę platformy Azure, do której chcesz się zalogować podczas logowania się do programu Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Synchronizowanie ustawień na wielu komputerach](../synchronized-settings-in-visual-studio.md)
- [Logowanie do programu Visual Studio](../signing-in-to-visual-studio.md)
- [Praca z wieloma kontami użytkowników](../work-with-multiple-user-accounts.md)
- [Ustawienia środowiska](../environment-settings.md)
