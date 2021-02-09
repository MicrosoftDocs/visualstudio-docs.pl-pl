---
title: Logowanie do programu Visual Studio
description: Dowiedz się, jak zalogować się do programu Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2bc45ae5732db5033a1b123ef18cda27c426fd6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878529"
---
# <a name="sign-in-to-visual-studio"></a>Logowanie do programu Visual Studio

Możesz spersonalizować i zoptymalizować środowisko programistyczne w programie Visual Studio, logując się do konta personalizacji.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz artykuł [Logowanie do usługi Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [! Ostrzeżenie] przy użyciu programu Visual Studio 2017 do uzyskiwania dostępu do zasobów skonfigurowanych dla dostępu warunkowego może wyzwolić niesprawne uwierzytelnianie, monitując o ponowne uwierzytelnienie kilka razy w ramach tej samej sesji programu Visual Studio. 
> Aby można było korzystać z zasobów skonfigurowanych do dostępu warunkowego, należy przeprowadzić uaktualnienie do programu Visual Studio 2019 Update 16,6 lub nowszego. Aby uzyskać więcej informacji, zobacz [jak używać programu Visual Studio z kontami, które wymagają uwierzytelniania wieloskładnikowego](work-with-multi-factor-authentication.md).

::: moniker-end

## <a name="why-should-i-sign-in-to-visual-studio"></a>Dlaczego powinienem się zarejestrować w usłudze Visual Studio?

Po zalogowaniu się możesz wzbogacić środowisko programu Visual Studio. Na przykład po zalogowaniu można [zsynchronizować ustawienia](synchronized-settings-in-visual-studio.md) między urządzeniami, zwiększyć okres próbny i automatycznie połączyć się z usługą platformy Azure, aby nazwać kilka.

Poniżej znajduje się pełna lista elementów, których można oczekiwać, oraz czynności, które można wykonać po zalogowaniu:
- **Zwiększ okres próbny programu Visual Studio** — możesz użyć Visual Studio Professional lub Visual Studio Enterprise przez dodatkowe 90 dni, a nie ograniczyć się do okresu próbnego 30 dni. Aby uzyskać więcej informacji, zobacz temat [zwiększanie wersji próbnej lub aktualizowanie licencji](../ide/how-to-unlock-visual-studio.md).

- **Kontynuuj korzystanie z programu Visual Studio Community Edition** — Jeśli w ramach instalacji Community zostanie wyświetlony komunikat z prośbą o licencję, zaloguj się do środowiska IDE, aby nadal **bezpłatnie** korzystać z programu Visual Studio Community. 

- **Odblokuj program Visual Studio, jeśli używasz konta skojarzonego z subskrypcją programu Visual Studio lub organizacją usługi Azure DevOps**. Aby uzyskać szczegółowe instrukcje, zobacz sekcję [zwiększanie wersji próbnej lub aktualizowanie licencji](../ide/how-to-unlock-visual-studio.md).

- **Dostęp do programu Visual Studio Dev Essentials** — ten program obejmuje bezpłatne oferty oprogramowania, szkolenia, pomoc techniczną i inne. Aby uzyskać więcej informacji, zobacz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) .

- **Zsynchronizuj ustawienia programu Visual Studio** — ustawienia, które można dostosować, takie jak powiązania klawiszy, układ okna i motyw kolorów, są stosowane natychmiast po zalogowaniu się do programu Visual Studio na dowolnym urządzeniu. Zobacz [Synchronizowanie ustawień w programie Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

- **Automatycznie łącz się z usługami takimi jak Azure i Azure DevOps Services** w środowisku IDE bez monitowania o poświadczenia dla tego samego konta.

## <a name="how-to-sign-in-to-visual-studio"></a>Jak zalogować się do programu Visual Studio

Po otwarciu programu Visual Studio po raz pierwszy zostanie wyświetlony monit o zalogowanie się i dostarczenie podstawowych informacji rejestracyjnych.

![Monit logowania](../ide/media/vs2019_signinpopup.png)

Należy wybrać konto Microsoft lub konto służbowe, które najlepiej reprezentuje użytkownika. Jeśli nie masz żadnego z tych kont, możesz utworzyć konto Microsoft bezpłatnie przez kliknięcie linku w obszarze przycisk Zaloguj. Jeśli masz problemy, zobacz Jak mogę utworzyć [konto w konto Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

Następnie wybierz ustawienia interfejsu użytkownika i kompozycję kolorów, których chcesz używać w programie Visual Studio. Program Visual Studio zapamiętuje te ustawienia i synchronizuje je we wszystkich środowiskach programu Visual Studio, do których się zalogowano. Aby zapoznać się z listą synchronizowanych ustawień, zobacz [Ustawienia zsynchronizowane](../ide/synchronized-settings-in-visual-studio.md). Możesz zmienić ustawienia później, jeśli otworzysz   >  menu **Opcje** narzędzi w programie Visual Studio.

Po podaniu ustawień program Visual Studio uruchomi się, zaloguje cię i umożliwi rozpoczęcie pracy. Aby sprawdzić, czy użytkownik jest zalogowany, poszukaj nazwy w prawym górnym rogu środowiska Visual Studio.

![Aktualnie zalogowany użytkownik w VS2019](../ide/media/vs2019_username.png)

Jeśli nie zdecydujesz się na zalogowanie się przy pierwszym otwarciu programu Visual Studio, można to zrobić później. Poszukaj linku **logowania** w prawym górnym rogu środowiska programu Visual Studio.

![Użytkownik niezalogowany](../ide/media/vs2019_usernotsignedin.png)

Jeśli nie wylogujesz się, nastąpi automatyczne zalogowanie do programu Visual Studio przy każdym jego uruchomieniu, a zmiany w synchronizowanych ustawieniach są automatycznie stosowane. Aby się wylogować, kliknij ikonę z nazwą profilu w prawym górnym rogu środowiska Visual Studio, wybierz polecenie **Ustawienia konta** , a następnie wybierz link **Wyloguj się** . Aby zalogować się ponownie, wybierz polecenie **Zaloguj** się w prawym górnym rogu środowiska programu Visual Studio.

## <a name="to-change-your-profile-information"></a>Aby zmienić informacje w profilu

1. Przejdź do pozycji  >  **Ustawienia konta** pliku i wybierz łącze **Zarządzaj profilem programu Visual Studio** .

1. W oknie przeglądarki wybierz pozycję **Edytuj profil** i Zmień ustawienia, które chcesz.

1. Gdy skończysz, wybierz pozycję **Zapisz zmiany**.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli podczas logowania wystąpią jakiekolwiek problemy, skontaktuj się z [pomocą techniczną](https://visualstudio.microsoft.com/subscriptions/support/) , aby uzyskać pomoc.

## <a name="see-also"></a>Zobacz też

* [Rozszerzanie wersji próbnej lub aktualizowanie licencji](../ide/how-to-unlock-visual-studio.md)
* [Praca z kontami usługi GitHub w programie Visual Studio](../ide/work-with-github-accounts.md)
* [Środowisko IDE programu Visual Studio — omówienie](../get-started/visual-studio-ide.md)
* [Logowanie (Visual Studio dla komputerów Mac)](/visualstudio/mac/signing-in)
* [Aktywacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/activation)
