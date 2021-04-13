---
title: Praca z kontami usługi GitHub w programie Visual Studio
ms.date: 11/16/2020
ms.custom: ''
ms.topic: conceptual
description: Dowiedz się, jak używać programu Visual Studio z kontami usługi GitHub.
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9f55a233cc2550cd452851edc9092b4b2f4f2411
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296368"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Praca z kontami usługi GitHub w programie Visual Studio

Jeśli masz publiczne konto w serwisie GitHub lub GitHub Enterprise, możesz je dodać do łańcucha kluczy programu Visual Studio. Po dodaniu konta będziesz mieć możliwość skorzystania z integracji z platformą, uzyskując dostęp do repozytoriów usługi GitHub i tworząc je bezpośrednio z programu Visual Studio.

## <a name="adding-public-github-accounts"></a>Dodawanie publicznych kont usługi GitHub

Możesz dodać swoje publiczne konto usługi GitHub, jeśli użytkownik jest już zalogowany do programu Visual Studio przy użyciu konto Microsoft lub konta służbowego.

1. Wybierz ikonę z inicjałami w prawym górnym rogu środowiska programu Visual Studio. Następnie wybierz pozycję **Ustawienia konta..** ., aby zarządzać kontami. Możesz również otworzyć okno dialogowe Ustawienia konta, przechodząc do   >  **ustawień konta** pliku.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Ustawienia konta":::

2. W podmenu **wszystkie konta** wybierz znak plus, aby dodać konto, a następnie wybierz pozycję **GitHub**.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Wybierz pozycję Dodaj konto usługi GitHub":::

3. Nastąpi przekierowanie do przeglądarki, w której możesz zalogować się przy użyciu poświadczeń usługi GitHub. Po zalogowaniu zostanie wyświetlone okno z sukcesem w przeglądarce i można wrócić do programu Visual Studio.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Okno sukcesu w przeglądarce":::

4. Wszystkie konta będą obecne w podmenu **wszystkie konta** .

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Wyświetlane są oba konta":::

Jeśli jeszcze nie zalogowano się do programu Visual Studio przy użyciu innego konta, wybierz link **Zaloguj** w prawym górnym rogu środowiska programu Visual Studio. Możesz również otworzyć okno dialogowe Ustawienia konta, przechodząc do   >  **ustawień konta** pliku. Następnie postępuj zgodnie z powyższymi instrukcjami, aby dodać konto usługi GitHub.

![Użytkownik niezalogowany](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Dodawanie kont przedsiębiorstwa usługi GitHub

Domyślnie program Visual Studio ma włączone publiczne konta serwisu GitHub.

1. Aby włączyć konta w usłudze GitHub Enterprise, przejdź do  >  **opcji** narzędzia i Wyszukaj opcje **konta** .

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Menu Opcje kont":::

2. Następnie zaznacz pole wyboru, aby **dołączyć konta serwera usługi GitHub dla przedsiębiorstw**. Przy następnym przejściu do **ustawień konta** i ponowieniu próby dodania konta usługi GitHub zobaczysz opcje dla przedsiębiorstwa w serwisie GitHub i GitHub.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Logowanie za pomocą usługi GitHub Enterprise":::

3. Po wprowadzeniu adresu serwera w witrynie GitHub Enterprise wybierz pozycję **Zaloguj się za pomocą przeglądarki**. W tym miejscu możesz zalogować się przy użyciu poświadczeń przedsiębiorstwa usługi GitHub.

## <a name="see-also"></a>Zobacz też

- [Praca z wieloma kontami użytkowników](work-with-multiple-user-accounts.md)
- [Logowanie do programu Visual Studio](signing-in-to-visual-studio.md)
