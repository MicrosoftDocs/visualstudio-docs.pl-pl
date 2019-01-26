---
title: Odwołanie do konta opcje
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b99a75579f63dd19de74c6d5bc3c13a2833bc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996121"
---
# <a name="accounts-environment-options-dialog-box"></a>Konta, środowisko, opcje, okno dialogowe

Ta strona służy do ustawiania różne opcje związane z kontami, których używasz do logowania do programu Visual Studio.

## <a name="personalization-account"></a>Konto personalizacji

### <a name="synchronize-settings-across-devices"></a>Synchronizacja ustawień między urządzeniami

Użyj tej opcji, aby określić, czy synchronizację ustawień między wieloma maszynami. Aby uzyskać więcej informacji, zobacz [zsynchronizowane ustawienia](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Włącz przepływ kodu urządzenia

Gdy ta opcja jest zaznaczona, zmienia się zachowanie programu Visual Studio po wybraniu **Dodaj konto** na **pliku** > **ustawienia konta** strony. Zamiast zobaczyć **Zaloguj się do swojego konta** stronie zostanie wyświetlone okno dialogowe, które udostępnia adres URL i kodu Wklej w przeglądarce sieci web Zaloguj się. Ta opcja jest przydatna w przypadkach, w których nie możesz zalogować do programu Visual Studio w zwykły sposób, na przykład, jeśli używasz starszej wersji programu Internet Explorer, czy Zapora ogranicza dostęp. Aby uzyskać więcej informacji, zobacz [Praca z wieloma kontami użytkownika](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Zarejestrowane chmury platformy Azure

W tej sekcji przedstawiono wystąpienia platformy Azure w chmurze, czy masz dostęp do za pośrednictwem jednego lub większej liczby kont, których używasz do logowania do programu Visual Studio. Na przykład może być dostęp do prywatnej wystąpienie platformy Azure w centrum danych firmy. Lub możesz mieć dostęp do platformy Azure, takich jak Azure wystąpienia suwerennych lub dla instytucji rządowych w Stanach Zjednoczonych (Chiny) lub Azure Dla instytucji rządowych. Wystąpienia globalnego chmury platformy Azure są wyświetlane domyślnie na liście, a nie można go usunąć.

Zarejestruj się dodatkowe platformy Azure w chmurze, wybierając **Dodaj** przycisku. **Dodawanie nowej chmury Azure** okno dialogowe wyświetla kilka wystąpień dobrze znanych chmury platformy Azure, możesz nawiązać połączenie, lub wprowadź adres URL prywatnego punkt końcowy platformy Azure.

![Dodaj nowe wystąpienie w chmurze platformy Azure](media/add-new-azure-cloud.png)

Po zarejestrowaniu dodatkowe chmurze platformy Azure, możesz wybrać, jaka chmura platformy Azure, aby logować się po zalogowaniu do programu Visual Studio.

## <a name="see-also"></a>Zobacz także

- [Synchronizacja ustawień na wielu komputerach](../synchronized-settings-in-visual-studio.md)
- [Logowanie do programu Visual Studio](../signing-in-to-visual-studio.md)
- [Praca z wieloma kontami użytkowników](../work-with-multiple-user-accounts.md)
- [Ustawienia środowiska](../environment-settings.md)
- [Okno dialogowe opcji środowiska](../../ide/reference/environment-options-dialog-box.md)