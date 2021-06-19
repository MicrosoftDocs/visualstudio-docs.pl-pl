---
title: Logowanie w systemie Windows
description: Dowiedz się, jak zalogować się do Visual Studio.
titleSuffix: ''
ms.custom: seodec18, contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b0ed679188cc0a4df9329fdd0adff4ad69667e6
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375763"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Zaloguj się do aplikacji Visual Studio systemie Windows

Chociaż nie musisz się logować, ma to wiele zalet. Po zalogowaniu się możesz personalizować, optymalizować i wzbogacać środowisko Visual Studio użytkownika. 

> [!NOTE]
> Ten temat dotyczy Visual Studio systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Logowanie się do Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> Aby pracować z zasobami skonfigurowanymi do dostępu warunkowego, uaktualnij program do wersji Visual Studio 2019 Update 16.6 lub nowszej. Aby uzyskać więcej informacji, zobacz Jak używać usługi [Visual Studio z kontami, które wymagają uwierzytelniania wieloskładnikowego.](work-with-multi-factor-authentication.md)
> Używanie programu Visual Studio 2017 do uzyskiwania dostępu do zasobów skonfigurowanych do dostępu warunkowego może wyzwolić środowisko uwierzytelniania z obniżoną wydajnością, kilkukrotnie monitując o ponowne uwierzytelnienie w ramach tej samej Visual Studio sesji. 
> 
::: moniker-end

## <a name="benefits"></a>Korzyści

Oto pełna lista tego, czego można oczekiwać i co można zrobić po zalogowaniu się:


#### <a name="extend-the-visual-studio-trial-period"></a>Przedłużenie okresu Visual Studio próbnego

Możesz używać Visual Studio Professional lub Visual Studio Enterprise przez dodatkowe 90 dni, zamiast ograniczać się do okresu próbnego 30 dni. Aby uzyskać więcej informacji, zobacz [Rozszerzanie wersji próbnej lub aktualizowanie licencji](../ide/how-to-unlock-visual-studio.md).

#### <a name="synchronize-your-visual-studio-settings"></a>Synchronizowanie ustawień Visual Studio użytkownika

Ustawienia, które można dostosować, takie jak powiązania klawiszy, układ okna i motyw kolorów, są stosowane natychmiast po zalogowaniu się do Visual Studio dowolnym urządzeniu. Zobacz [Synchronize settings in Visual Studio (Synchronizowanie ustawień w Visual Studio](../ide/synchronized-settings-in-visual-studio.md)).

#### <a name="use-visual-studio-community-edition"></a>Korzystanie Visual Studio Community wersji

Jeśli podczas instalacji wersji Community Edition zostanie wyświetlony monit o licencję, zaloguj się do środowiska IDE, aby nadal korzystać Visual Studio Community **bezpłatnie.** 

#### <a name="unlock-visual-studio-visual-studio-subscription-or-an-azure-devops-organization"></a>Odblokowywanie Visual Studio (Visual Studio subskrypcji lub Azure DevOps organizacji)

Odblokuj Visual Studio, jeśli używasz konta skojarzonego z subskrypcją usługi Visual Studio lub organizacją Azure DevOps, korzystając z procedury rozszerzania wersji próbnej lub [aktualizowania licencji.](../ide/how-to-unlock-visual-studio.md)

#### <a name="the-visual-studio-dev-essentials-program"></a>Program Visual Studio Dev Essentials programu

Ten program obejmuje bezpłatne oferty oprogramowania, szkolenia, pomoc techniczną i nie tylko. Zobacz [Visual Studio Dev Essentials,](https://visualstudio.microsoft.com/dev-essentials/) aby uzyskać więcej informacji.

#### <a name="automatically-connect-to-services"></a>Automatyczne łączenie z usługami

Połącz się z usługami, takimi jak azure i Azure DevOps Services, w idee ide bez konieczności monitowania o poświadczenia dla tego samego konta.

## <a name="how-to-sign-in"></a>Jak się zalogować 

Po pierwszym otwarciu Visual Studio użytkownik zostanie poproszony o zalogowanie się i podanie podstawowych informacji dotyczących rejestracji.

![Monit logowania](../ide/media/vs2019_signinpopup.png)

1. Wybierz konto konto Microsoft konto służbowe, które najlepiej Cię reprezentuje. Jeśli nie masz żadnego z tych kont, możesz bezpłatnie utworzyć konto konto Microsoft klikając link pod przyciskiem logowania. Jeśli masz problemy, zobacz Jak mogę [się, aby uzyskać konto Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Wybierz ustawienia interfejsu użytkownika i motyw kolorów, których chcesz użyć w Visual Studio. Visual Studio zapamiętuje te ustawienia i synchronizuje je Visual Studio wszystkich środowiskach, do których się zalogowano. Aby uzyskać listę zsynchronizowanych ustawień, zobacz [Synchronized settings (Zsynchronizowane ustawienia).](../ide/synchronized-settings-in-visual-studio.md) Ustawienia można zmienić później, jeśli otworzysz menu Opcje  >  **narzędzi** w Visual Studio.
   Po podaniu ustawień program Visual Studio uruchomi się, zaloguje cię i umożliwi rozpoczęcie pracy. 
   
1. Aby sprawdzić, czy zalogowano się, poszukaj swojej nazwy w prawym górnym rogu Visual Studio aplikacji.

![Obecnie zalogowany użytkownik w programie VS2019](../ide/media/vs2019_username.png)

Jeśli zdecydujesz się nie logować się przy pierwszym otwarciu Visual Studio, będzie to łatwe później. Poszukaj **linku Sign in (Zaloguj** się) w prawym górnym rogu Visual Studio środowiska.

![Nie zalogowano użytkownika](../ide/media/vs2019_usernotsignedin.png)

O ile się nie wylogujesz, użytkownik jest automatycznie logowany do witryny Visual Studio przy każdym uruchomieniu, a wszelkie zmiany zsynchronizowanych ustawień są automatycznie stosowane. Aby się wylogować, kliknij ikonę z nazwą profilu w prawym górnym rogu środowiska usługi Visual Studio, wybierz polecenie **Ustawienia** konta, a następnie wybierz **link** Wyloguj. Aby zalogować się ponownie, wybierz **polecenie Zaloguj** się w prawym górnym rogu Visual Studio użytkownika.

## <a name="update-your-profile"></a>Aktualizowanie profilu

1. Przejdź do **opcji**  >  **Ustawienia konta** pliku i wybierz link Visual Studio **profilu.**

1. W oknie przeglądarki wybierz **pozycję Edytuj profil** i zmień ustawienia.

1. Gdy wszystko będzie gotowe, wybierz pozycję **Zapisz zmiany.**

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Aby uzyskać [pomoc,](https://visualstudio.microsoft.com/subscriptions/support/) zobacz stronę Pomoc techniczna dla subskrypcji.

## <a name="see-also"></a>Zobacz też

* [Rozszerzanie wersji próbnej lub aktualizowanie licencji](../ide/how-to-unlock-visual-studio.md)
* [Praca z kontami usługi GitHub w programie Visual Studio](../ide/work-with-github-accounts.md)
* [omówienie Visual Studio IDE](../get-started/visual-studio-ide.md)
