---
description: Począwszy od programu Visual Studio 2019 w wersji 16,8, można użyć narzędzia do publikowania do publikowania programu .NET Core 3,1 lub nowszego, aplikacji klasycznych systemu Windows przy użyciu technologii ClickOnce z programu Visual Studio.
title: Wdrażanie aplikacji klasycznej systemu Windows z użyciem technologii ClickOnce
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: d3977408f191aabc734226fd6b637fcfaaf5e9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165712"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>Wdrażanie aplikacji klasycznej systemu Windows z użyciem technologii ClickOnce

Począwszy od programu Visual Studio 2019 w wersji 16,8, można użyć narzędzia do **publikowania** do publikowania programu .net Core 3,1 lub nowszego, aplikacji klasycznych systemu Windows przy użyciu technologii ClickOnce z programu Visual Studio.

> [!NOTE]
> Jeśli musisz opublikować .NET Framework aplikację systemu Windows, zobacz [wdrażanie aplikacji klasycznej przy użyciu technologii ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# lub Visual Basic).

## <a name="publishing-with-clickonce"></a>Publikowanie przy użyciu technologii ClickOnce

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Publikuj** (lub użyj elementu menu **Kompiluj**  >  **publikację** ).

    ![Polecenie Publikuj w menu kontekstowym projektu w Eksplorator rozwiązań](../deployment/media/quickstart-clickonce-solution-explorer.png "Wybierz pozycję Publikuj")

1. Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlona strona **Publikowanie** . Wybierz pozycję **Nowy**.

1. W kreatorze **publikacji** wybierz pozycję **folder**.

    ![Wybierz folder jako element docelowy publikowania](../deployment/media/quickstart-clickonce-publish-folder-category.png "Wybierz folder")

1. Na stronie **określony cel** wybierz opcję **ClickOnce**.

    ![Wybierz ClickOnce jako konkretny element docelowy](../deployment/media/quickstart-clickonce-publish-folder-target.png "Wybierz ClickOnce")

1. Wprowadź ścieżkę lub wybierz pozycję **Przeglądaj** , aby wybrać lokalizację publikacji.

    ![Określ ścieżkę do lokalizacji publikowania](../deployment/media/quickstart-clickonce-publish-location.png "Wprowadź ścieżkę")

1. Na stronie **Lokalizacja instalacji** wybierz, gdzie użytkownicy będą instalować aplikację.

    ![Określ ścieżkę do folderu](../deployment/media/quickstart-clickonce-install-location.png "Wybierz lokalizację instalacji")

1. Na stronie **Ustawienia** można podać ustawienia wymagane dla technologii ClickOnce.

1. Jeśli wybrano opcję instalacji ze ścieżki UNC lub witryny sieci Web, na tej stronie można określić, czy aplikacja jest dostępna w trybie offline. Po wybraniu tej opcji będzie można wyświetlić listę aplikacji w menu Start użytkowników i umożliwi ona automatyczną aktualizację aplikacji po opublikowaniu nowej wersji. Domyślnie aktualizacje są dostępne w lokalizacji instalacji.  Jeśli chcesz mieć inną lokalizację aktualizacji, możesz określić, korzystając z linku Ustawienia aktualizacji. Jeśli nie chcesz, aby aplikacja była dostępna w trybie offline, zostanie uruchomiona z lokalizacji instalacji.

    ![Określ ustawienia publikowania](../deployment/media/quickstart-clickonce-unc-settings.png "Wybieranie ustawień publikowania")

1. Jeśli wybrano opcję instalacji z dysku CD, DVD lub USB, ta strona umożliwia również określenie, czy aplikacja obsługuje aktualizacje automatyczne. W przypadku wybrania opcji obsługi aktualizacji wymagana jest lokalizacja aktualizacji, która musi być prawidłową ścieżką UNC lub witryną sieci Web.

    ![Wybieranie ustawień publikowania](../deployment/media/quickstart-clickonce-settings.png "Wybieranie ustawień publikowania")

Na tej stronie można określić, które **pliki aplikacji** mają być uwzględnione w instalatorze, które pakiety **wstępnie wymagane** do zainstalowania, oraz inne **Opcje** za pośrednictwem linków w górnej części strony.

Na tej stronie można również ustawić wersję publikacji i, jeśli wersja zostanie automatycznie zwiększona przy każdej publikacji.

> [!NOTE]
> Numer wersji publikacji jest unikatowy dla każdego profilu ClickOnce. Jeśli planujesz posiadanie więcej niż jednego profilu, musisz mieć na uwadze.

10. Na stronie **Podpisz manifesty** możesz określić, czy manifesty mają być podpisane i których certyfikatu użyć.

    ![Podpisywanie manifestów ClickOnce](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. Na stronie **Konfiguracja** można wybrać żądaną konfigurację projektu.

     ![Określ konfigurację publikacji](../deployment/media/quickstart-clickonce-configuration.png)

    Aby uzyskać dodatkową pomoc dotyczącą wyboru ustawienia, zobacz następujące tematy:

    - [Wdrażanie zależne od platformy a wdrożenie samodzielne](/dotnet/core/deploying/)
    - [Docelowe identyfikatory środowiska uruchomieniowego (Portable RID, et al)](/dotnet/core/rid-catalog)
    - [Konfiguracje debugowania i wydania](../ide/understanding-build-configurations.md)

1. Wybierz pozycję **Zakończ** , aby zapisać nowy profil publikowania technologii ClickOnce.

1. Na stronie **Podsumowanie** wybierz pozycję **Publikuj** , a program Visual Studio kompiluje projekt i opublikuje go w określonym folderze publikacji. Ta strona zawiera również podsumowanie profilu.

    ![Okienko właściwości publikowania przedstawiające Podsumowanie profilu](../deployment/media/quickstart-clickonce-summary.png)

1. Aby ponownie opublikować, wybierz pozycję **Publikuj**.

## <a name="next-steps"></a>Następne kroki

W przypadku aplikacji .NET:

- [Wdrażanie .NET Framework i aplikacji](/dotnet/framework/deployment/)
- [Dokumentacja technologii ClickOnce](clickonce-reference.md)
