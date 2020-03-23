---
title: Logowanie do programu Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 03/10/2020
ms.topic: conceptual
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1033d4167c03951a642656807aeb9cca83116651
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79132717"
---
# <a name="sign-in-to-visual-studio"></a>Logowanie do programu Visual Studio

Możesz spersonalizować i zoptymalizować środowisko programistyczne w programie Visual Studio, logując się na swoje konto personalizacji.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. Aby zapoznać się z programem Visual Studio dla komputerów Mac, zobacz [Logowanie się do programu Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in).

## <a name="why-should-i-sign-in-to-visual-studio"></a>Dlaczego powinienem się zarejestrować w usłudze Visual Studio?

Po zalogowaniu się wzbogacić środowisko programu Visual Studio. Na przykład po zalogowaniu można [zsynchronizować ustawienia](synchronized-settings-in-visual-studio.md) między urządzeniami, rozszerzyć wersję próbną i automatycznie połączyć się z usługą platformy Azure, aby wymienić tylko kilka.

Oto pełna lista tego, czego możesz się spodziewać i co możesz zrobić po zalogowaniu się:
- **Przedłuż okres próbny programu Visual Studio** — program Visual Studio Professional lub Visual Studio Enterprise można używać przez dodatkowe 90 dni, zamiast ograniczać się do okresu próbnego wynoszącego 30 dni. Aby uzyskać więcej informacji, zobacz [Rozszerzanie wersji próbnej lub aktualizowanie licencji](../ide/how-to-unlock-visual-studio.md).

- **Odblokuj wersję społeczności programu Visual Studio** — jeśli instalacja wersji społecznościowej monituje o licencję, zaloguj się do IDE, aby odblokować siebie.

- **Odblokuj program Visual Studio, jeśli używasz konta skojarzonego z subskrypcją programu Visual Studio lub organizacją Azure DevOps.** Aby uzyskać szczegółowe instrukcje, zobacz [Rozszerzanie wersji próbnej lub aktualizowanie licencji](../ide/how-to-unlock-visual-studio.md).

- **Dostęp do programu Visual Studio Dev Essentials** — ten program zawiera oferty wolnego oprogramowania, szkolenia, wsparcie i inne. Aby uzyskać więcej informacji, zobacz [Podstawowe informacje dotyczące programu Visual Studio Dev.](https://visualstudio.microsoft.com/dev-essentials/)

- **Synchronizuj ustawienia programu Visual Studio** — ustawienia, które można dostosować, takie jak powiązania kluczy, układ okna i motyw kolorów, stosuje się natychmiast po zalogowaniu się do programu Visual Studio na dowolnym urządzeniu. Zobacz [Synchronizowanie ustawień w programie Visual Studio](../ide/synchronized-settings-in-visual-studio.md).

- **Automatyczne łączenie się z usługami, takimi jak Azure i usługi Azure DevOps** w usłudze IDE bez ponownego monitowania o poświadczenia dla tego samego konta.

## <a name="how-to-sign-in-to-visual-studio"></a>Jak zalogować się do programu Visual Studio

Po otwarciu programu Visual Studio po raz pierwszy zostaniesz poproszony o zalogowanie się i podanie podstawowych informacji rejestracyjnych. 

![Monit o logowanie](../ide/media/vs2019_signinpopup.png)

Należy wybrać konto Microsoft lub konto służbowe, które najlepiej Cię reprezentuje. Jeśli nie masz żadnego z tych kont, możesz utworzyć konto Microsoft za darmo, klikając łącze pod przyciskiem logowania. Jeśli masz problemy, zobacz [Jak zarejestrować konto Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

Następnie wybierz ustawienia interfejsu użytkownika i kompozycję kolorów, których chcesz używać w programie Visual Studio. Program Visual Studio zapamiętuje te ustawienia i synchronizuje je we wszystkich środowiskach programu Visual Studio, do których się zalogowano. Aby uzyskać listę ustawień, które są synchronizowane, zobacz [Ustawienia zsynchronizowane](../ide/synchronized-settings-in-visual-studio.md). Ustawienia można zmienić później, jeśli otworzysz menu**Opcje** **narzędzi** > w programie Visual Studio.

Po podaniu ustawień program Visual Studio uruchomi się, zaloguje cię i umożliwi rozpoczęcie pracy. Aby sprawdzić, czy jesteś zalogowany, poszukaj swojego imienia i nazwiska w prawym górnym rogu środowiska programu Visual Studio.

![Aktualnie zalogowany użytkownik w VS2019](../ide/media/vs2019_username.png)

Jeśli nie chcesz się logować przy pierwszym otwarciu programu Visual Studio, można to zrobić później. Poszukaj **łącza Zaloguj** się w prawym górnym rogu środowiska programu Visual Studio. 

![Nie zalogowany użytkownik](../ide/media/vs2019_usernotsignedin.png)

Jeśli nie wylogujesz się, automatycznie zalogujesz się do programu Visual Studio przy każdym uruchomieniu, a wszelkie zmiany w zsynchronizowanych ustawieniach są automatycznie stosowane. Aby się wylogować, kliknij ikonę z nazwą profilu w prawym górnym rogu środowiska programu Visual Studio, wybierz polecenie **Ustawienia konta,** a następnie wybierz łącze **Wyloguj.** Aby zalogować się ponownie, wybierz polecenie Zaloguj się **w** prawym górnym rogu środowiska programu Visual Studio.

## <a name="to-change-your-profile-information"></a>Aby zmienić informacje w profilu

1. Przejdź do pozycji**Ustawienia konta** **plików** > i wybierz łącze **Profil zarządzania programem Visual Studio.**

1. W oknie przeglądarki wybierz pozycję **Edytuj profil** i zmień żądane ustawienia.

1. Po zakończeniu wybierz pozycję **Zapisz zmiany**.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli podczas logowania występują jakiekolwiek problemy, skorzystaj ze strony [Pomocy technicznej dla subskrypcji,](https://visualstudio.microsoft.com/subscriptions/support/) aby uzyskać pomoc.

## <a name="see-also"></a>Zobacz też

* [Rozszerzanie wersji próbnej lub aktualizowanie licencji](../ide/how-to-unlock-visual-studio.md)
* [Omówienie ide programu Visual Studio](../get-started/visual-studio-ide.md)
* [Zaloguj się (Visual Studio dla komputerów Mac)](/visualstudio/mac/signing-in)
* [Aktywacja (Visual Studio dla komputerów Mac)](/visualstudio/mac/activation)
