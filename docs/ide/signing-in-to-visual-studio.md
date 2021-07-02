---
title: Zaloguj
description: Dowiedz się, jak zalogować się do Visual Studio.
ms.custom: contperf-fy21q1
ms.date: 09/11/2020
ms.topic: how-to
ms.assetid: b9531c25-e4cf-43ae-b331-a9f31a8cd171
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1335ab3d8f679f00fb7f52420d378baa1f2bd905
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222997"
---
# <a name="sign-in-to-visual-studio-on-windows"></a>Zaloguj się do Visual Studio na Windows

Chociaż nie musisz się logować, możesz to zrobić z wieloma korzyściami. Po zalogowaniu się możesz personalizować, optymalizować i wzbogacać środowisko Visual Studio użytkownika. 

> [!NOTE]
> Ten temat dotyczy Visual Studio na Windows. Aby Visual Studio dla komputerów Mac, zobacz [Logowanie do Visual Studio dla komputerów Mac](/visualstudio/mac/signing-in).

::: moniker range="vs-2017"

> [!WARNING]
> Aby pracować z zasobami skonfigurowanymi do dostępu warunkowego, uaktualnij program do wersji Visual Studio 2019 Update 16.6 lub nowszej. Aby uzyskać więcej informacji, zobacz Jak używać usługi [Visual Studio z kontami, które wymagają uwierzytelniania wieloskładnikowego.](work-with-multi-factor-authentication.md)
> Używanie programu Visual Studio 2017 do uzyskiwania dostępu do zasobów skonfigurowanych na dostęp warunkowy może spowodować obniżenie wydajności uwierzytelniania, co powoduje kilkukrotnie monitowanie o ponowne uwierzytelnienie w ramach tej samej Visual Studio dostępu. 
> 
::: moniker-end

## <a name="benefits"></a>Korzyści

Oto pełna lista tego, czego można oczekiwać i co można zrobić po zalogowaniu się:

|Korzyść|Opis|
|---|---|
|Przedłużenie okresu Visual Studio próbnego|Używaj Visual Studio Professional lub Visual Studio Enterprise przez **dodatkowe 90** dni, zamiast ograniczać się do okresu próbnego 30 dni. <br/>Zobacz [Rozszerzanie wersji próbnej lub aktualizowanie licencji.](../ide/how-to-unlock-visual-studio.md)|
|Odblokowywanie Visual Studio (Visual Studio subskrypcji lub Azure DevOps organizacji)|Odblokuj Visual Studio, jeśli używasz konta skojarzonego z subskrypcją Visual Studio lub Azure DevOps organizacji.<br/>Zobacz [Rozszerzanie wersji próbnej lub aktualizowanie licencji.](../ide/how-to-unlock-visual-studio.md)|
|Synchronizowanie ustawień Visual Studio użytkownika|Ustawienia dostosowania, takie jak powiązania klawiszy, układ okna i motyw kolorów, są stosowane natychmiast po zalogowaniu się do Visual Studio dowolnym urządzeniu. <br/>Zobacz [Synchronize settings in Visual Studio (Synchronizowanie ustawień w Visual Studio](../ide/synchronized-settings-in-visual-studio.md)).|
|Automatyczne łączenie z usługami|Połączenie usług, takich jak Azure i Azure DevOps Services, w idee IDE bez konieczności monitowania o poświadczenia dla tego samego konta.|
|Kontynuuj korzystanie z Visual Studio Community edition|Jeśli podczas instalacji Community edition zostanie wyświetlony monit o licencję, zaloguj się do środowiska IDE, aby nadal korzystać Visual Studio Community **bezpłatnie.** |
|Pobierz "Visual Studio Dev Essentials"|Ten program obejmuje bezpłatne oferty oprogramowania, szkolenia, pomoc techniczną i nie tylko. <br/>Zobacz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/).|


## <a name="how-to-sign-in"></a>Jak się zalogować 

Po pierwszym otwarciu Visual Studio użytkownik zostanie poproszony o zalogowanie się i podanie podstawowych informacji dotyczących rejestracji.

![Monit o zalogowanie](../ide/media/vs2019_signinpopup.png)

1. Wybierz konto konto Microsoft konto służbowe, które najlepiej Cię reprezentuje. Jeśli nie masz żadnego z tych kont, możesz bezpłatnie utworzyć konto konto Microsoft klikając link pod przyciskiem logowania. Jeśli masz problemy, zobacz Jak mogę rejestracji w [celu konto Microsoft?](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create)

2. Wybierz ustawienia interfejsu użytkownika i motyw kolorów, których chcesz użyć w Visual Studio. Visual Studio zapamiętuje te ustawienia i synchronizuje je we wszystkich Visual Studio środowiskach, w których się zalogowano. Aby uzyskać listę synchronizowanych ustawień, zobacz [Synchronizowane ustawienia](../ide/synchronized-settings-in-visual-studio.md). Ustawienia można zmienić później, jeśli otworzysz menu Opcje  >  **narzędzi** w Visual Studio.
   Po podaniu ustawień program Visual Studio uruchomi się, zaloguje cię i umożliwi rozpoczęcie pracy. 
   
1. Aby sprawdzić, czy użytkownik jest zalogowany, poszukaj swojej nazwy w prawym górnym rogu Visual Studio środowiska.

![Obecnie zalogowany użytkownik w programie VS2019](../ide/media/vs2019_username.png)

Jeśli zdecydujesz się nie logować się przy pierwszym otwarciu Visual Studio, będzie to łatwe później. Poszukaj **linku Zaloguj** się w prawym górnym rogu Visual Studio środowiska.

![Nie zalogowano użytkownika](../ide/media/vs2019_usernotsignedin.png)

Jeśli się nie wylogujesz, użytkownik jest automatycznie logowany do aplikacji Visual Studio każdym uruchomieniu, a wszelkie zmiany zsynchronizowanych ustawień są automatycznie stosowane. Aby się wylogować, kliknij ikonę z nazwą profilu w prawym górnym rogu środowiska usługi Visual Studio, wybierz polecenie **Ustawienia** konta, a następnie wybierz **link** Wyloguj. Aby zalogować się ponownie, wybierz polecenie **Zaloguj** się w prawym górnym rogu Visual Studio użytkownika.

## <a name="update-your-profile"></a>Aktualizowanie profilu

1. Przejdź do **strony**  >  **Konto Ustawienia** i wybierz link Visual Studio profilu **plików.**

1. W oknie przeglądarki wybierz pozycję **Edytuj profil** i zmień ustawienia.

1. Gdy wszystko będzie gotowe, wybierz pozycję **Zapisz zmiany.**

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Aby uzyskać [pomoc,](https://visualstudio.microsoft.com/subscriptions/support/) zobacz stronę Pomocy technicznej dla subskrypcji.
