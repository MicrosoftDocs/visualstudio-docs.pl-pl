---
title: 'Przewodnik: Publikowanie rozszerzenia programu Visual Studio | Microsoft Docs'
description: Dowiedz się, jak opublikować rozszerzenie programu Visual Studio w celu Visual Studio Marketplace, co umożliwia deweloperom przeglądanie w poszukiwaniu nowych i zaktualizowanych rozszerzeń.
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b1ff7d55f7d667ca8b07134e144ad192b9d19d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078360"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Przewodnik: Publikowanie rozszerzenia programu Visual Studio

W tym instruktażu przedstawiono sposób publikowania rozszerzenia programu Visual Studio w celu Visual Studio Marketplace. Po dodaniu rozszerzenia do Visual Studio Marketplace deweloperzy mogą używać **rozszerzeń i aktualizacji** , aby wyszukiwać nowe i zaktualizowane rozszerzenia.

## <a name="prerequisites"></a>Wymagania wstępne

 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Utwórz rozszerzenie programu Visual Studio

W tym artykule jest używane domyślne rozszerzenie pakietu VSPackage, ale kroki są prawidłowe dla każdego rodzaju rozszerzenia.

- Utwórz element pakietu VSPackage w języku C# o nazwie `TestPublish` , który ma polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie pierwszego rozszerzenia: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Pakowanie rozszerzenia

1. Zaktualizuj rozszerzenie *. vsixmanifest* , podając prawidłowe informacje dotyczące nazwy produktu, autora i wersji.

   ![Aktualizacja rozszerzenia vsixmanifest](media/update-extension-vsixmanifest.png)

2. Kompiluj swoje rozszerzenie w trybie **wydania** . Teraz Twoje rozszerzenie jest spakowane jako VSIX w folderze \bin\Release.

3. Aby zweryfikować instalację, można kliknąć dwukrotnie VSIX.

## <a name="test-the-extension"></a>Testowanie rozszerzenia

 Przed rozpoczęciem dystrybucji rozszerzenia Skompiluj i przetestuj je, aby upewnić się, że jest poprawnie zainstalowana w eksperymentalnym wystąpieniu programu Visual Studio.

1. W programie Visual Studio Rozpocznij debugowanie, aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

2. W eksperymentalnym wystąpieniu przejdź do menu **Narzędzia** , a następnie kliknij pozycję **rozszerzenia i aktualizacje**. Rozszerzenie TestPublish powinno pojawić się w środkowym okienku i być włączone.

3. W menu **Narzędzia** upewnij się, że widzisz polecenie Test.

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>Opublikuj rozszerzenie, aby Visual Studio Marketplace

1. Upewnij się, że masz wbudowaną wersję wydania rozszerzenia oraz że jest ona aktualna.

2. W przeglądarce internetowej przejdź do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

3. W prawym górnym rogu kliknij pozycję **Zaloguj się**.

4. Zaloguj się przy użyciu konto Microsoft. Jeśli nie masz konto Microsoft, możesz go utworzyć w tym momencie.

5. Kliknij pozycję **Publikuj rozszerzenia**. Ta opcja umożliwia przejście do strony zarządzania dla wszystkich rozszerzeń. Jeśli nie masz konta wydawcy, zostanie wyświetlony monit o utworzenie jednego z nich.

   ![Przekaż do witryny Marketplace](media/upload-to-marketplace.png)

6. Wybierz wydawcę, którego chcesz użyć do przekazania rozszerzenia. Możesz zmienić wydawców, klikając nazwy wydawców z lewej strony. Kliknij pozycję **nowe rozszerzenie** i wybierz pozycję **Visual Studio**.

7. W **1: Przekaż rozszerzenie**, możesz przesłać plik VSIX bezpośrednio do Visual Studio Marketplace lub po prostu dodać link do własnej witryny sieci Web. W tym przykładzie zostanie przekazane rozszerzenie *TestPublish. vsix* . Przeciągnij i upuść rozszerzenie lub Użyj linku **kliknij** , aby wyszukać plik. Znajdź rozszerzenie w folderze \bin\Release projektu.  Kliknij przycisk **Kontynuuj**.

8. W **2: Podaj szczegóły rozszerzenia**, niektóre pola są wypełniane automatycznie z pliku *source. Extension. vsixmanifest* z Twojego rozszerzenia. Więcej szczegółowych informacji na ten temat znajduje się w poniższych tematach:

    * **Nazwa wewnętrzna** jest używana w adresie URL strony szczegółów rozszerzenia. Przykładowo opublikowanie rozszerzenia pod nazwą wydawcy "Moja nazwa" i określenie nazwy wewnętrznej do "My Extension" spowoduje wpisanie adresu URL "Marketplace. VisualStudio \. com/Items? itemName = ServiceName. my Extension" na stronie szczegółów rozszerzenia.

    * **Nazwa wyświetlana** rozszerzenia. Ta nazwa jest wypełniana automatycznie z pliku *source. Extension. vsixmanifest* .

    * Numer **wersji** przekazywanego rozszerzenia. Ta wersja jest wypełniana automatycznie z pliku *source. Extension. vsixmanifest* .

    * **Identyfikator VSIX** jest unikatowym identyfikatorem używanym przez program Visual Studio dla Twojego rozszerzenia. Ten identyfikator jest wymagany, jeśli chcesz, aby rozszerzenie zostało zaktualizowane. Ten identyfikator jest wypełniany automatycznie z pliku *source. Extension. vsixmanifest* .

    * **Logo** , które jest używane dla Twojego rozszerzenia. To logo jest wypełniane automatycznie z pliku *source. Extension. vsixmanifest* , jeśli jest podany.

    * **Krótki opis** działania Twojego rozszerzenia. Ten opis jest wypełniany automatycznie z pliku *source. Extension. vsixmanifest* .

    * **Omówienie** jest dobrym miejscem do uwzględnienia zrzutów ekranu i szczegółowych informacji o tym, co to jest rozszerzenie.

    * **Obsługiwane wersje programu Visual Studio** umożliwiają wybranie wersji programu Visual Studio, na których będzie działała Twoje rozszerzenie. Twoje rozszerzenie jest zainstalowane tylko w tych wersjach.

    * **Obsługiwana wersja programu Visual Studio** umożliwia wybranie wersji programu Visual Studio, na których będzie działała Twoje rozszerzenie. Twoje rozszerzenie jest zainstalowane tylko w tych wersjach.

    * **Typ**. Najbardziej typowym typem rozszerzenia jest **Narzędzia**.

    * **Kategorie**. Wybierz maksymalnie trzy, które najlepiej pasują do Twojego rozszerzenia.

    * **Tagi** są słowami kluczowymi, które pomagają użytkownikom znaleźć Twoje rozszerzenie. Tagi mogą pomóc zwiększyć istotność wyszukiwania rozszerzeń w Visual Studio Marketplace.

    * **Kategoria cennika** to koszt Twojego rozszerzenia.

    * **Repozytorium kodu źródłowego** umożliwia udostępnianie linku do kodu źródłowego społeczności.

    * **Zezwalaj na pytanie,&A dla rozszerzenia** umożliwia użytkownikom pozostawianie pytań na stronie wpisu rozszerzenia.

9. Kliknij przycisk **zapisz & Przekaż**. Ta opcja powoduje powrót do strony zarządzania wydawcami. Twoje rozszerzenie nie zostało jeszcze opublikowane.

10. Aby opublikować rozszerzenie, kliknij prawym przyciskiem myszy rozszerzenie i wybierz polecenie **Ustaw jako publiczne**. Aby zobaczyć, jak Twoje rozszerzenie będzie wyglądało Visual Studio Marketplace, wybierz pozycję **Wyświetl rozszerzenie**. W obszarze numery pozyskiwania kliknij pozycję **raporty**. Aby wprowadzić zmiany w rozszerzeniu, kliknij przycisk **Edytuj**.

    ![Menu wprowadzanie rozszerzenia](media/extension-entry-menu.png)

11. Kliknij przycisk **Ustaw jako publiczny** i Twoje rozszerzenie jest teraz publiczne. Wyszukaj Visual Studio Marketplace rozszerzenia.

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>Aktualizowanie opublikowanego rozszerzenia w Visual Studio Marketplace

Przed rozpoczęciem upewnij się, że została skompilowana Nowa wersja rozszerzenia i że jest ona aktualna.

1.  W przeglądarce internetowej przejdź do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

1.  W prawym górnym rogu kliknij pozycję **Zaloguj**, a następnie zaloguj się przy użyciu konto Microsoft.

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="Zrzut ekranu, który pokazuje Wybieranie przekazanego pliku rozszerzenia w Eksploratorze plików.":::

1.  Kliknij pozycję **Publikuj rozszerzenia**, a następnie wybierz wydawcę, którego chcesz użyć do przekazania zaktualizowanego rozszerzenia.

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="Zrzut ekranu przedstawiający Visual Studio Marketplace z wyróżnionym linkiem rozszerzeń publikowania.":::

1.  Obok rozszerzenia, które chcesz zaktualizować, umieść kursor myszy nad trzema kropkami w poziomie, a następnie wybierz pozycję **Edytuj**.

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="Zrzut ekranu pokazujący wybór rozszerzenia do edycji.":::

1.  W **1: Przekaż rozszerzenie**, po nazwie pliku VSIX kliknij ikonę ołówka, aby edytować opublikowane rozszerzenie.

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="Zrzut ekranu pokazujący kliknięcie ikony ołówka, aby edytować rozszerzenie.":::

1.  Przejdź do zaktualizowanego pliku VSIX rozszerzenia. Kliknij plik, a następnie kliknij przycisk **Otwórz**.

    Zaktualizowane rozszerzenie przekazuje.

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="Zrzut ekranu przedstawiający powiadomienie dotyczące przekazywania pliku po przekazaniu edytowanego rozszerzenia.":::

1. W **2: Podaj szczegóły rozszerzenia**, niektóre szczegóły są tylko do odczytu dla aktualizacji rozszerzenia lub są automatycznie wypełniane z poziomu rozszerzenia *source. Extension. vsixmanifest* . Poniżej znajduje się więcej informacji na temat szczegółów rozszerzenia:

    - **Nazwa wewnętrzna** \* jest używany w adresie URL strony szczegółów rozszerzenia. Przykładowo opublikowanie rozszerzenia pod nazwą wydawcy "Moja nazwa" i określenie nazwy wewnętrznej jako "My Extension" spowoduje wpisanie adresu URL "marketplace.visualstudio.com/items?itemName=myname.myextension" dla strony szczegółów rozszerzenia.

    - **Nazwa wyświetlana** \* rozszerzenia. Ta nazwa jest wypełniana automatycznie z pliku *source. Extension. vsixmanifest* .

    - **Wersja** \* Liczba przekazywanych rozszerzeń. Ta wersja jest wypełniana automatycznie z pliku *source. Extension. vsixmanifest* .

    - **Identyfikator VSIX** \* jest unikatowym identyfikatorem używanym przez program Visual Studio dla Twojego rozszerzenia. Ten identyfikator jest wymagany, jeśli chcesz, aby rozszerzenie zostało zaktualizowane. Ten identyfikator jest wypełniany automatycznie z pliku *source. Extension. vsixmanifest* .

    - **Logo** \* jest używany dla Twojego rozszerzenia. To logo jest wypełniane automatycznie z pliku *source. Extension. vsixmanifest* , jeśli jest podany.

    - **Krótki opis** \* tego, co Twoje rozszerzenie. Ten opis jest wypełniany automatycznie z pliku *source. Extension. vsixmanifest* .

    - **Omówienie** jest dobrym miejscem do uwzględnienia zrzutów ekranu i szczegółowych informacji o tym, co to jest rozszerzenie.

    - **Obsługiwane wersje** \* programu Visual Studio pozwala wybrać wersje programu Visual Studio, na których będzie działała Twoje rozszerzenie. Twoje rozszerzenie jest zainstalowane tylko w tych wersjach.

    - **Obsługiwana wersja** \* programu Visual Studio pozwala wybrać wersje programu Visual Studio, na których będzie działała Twoje rozszerzenie. Twoje rozszerzenie jest zainstalowane tylko w tych wersjach.

    - **Typ**. Najbardziej typowym typem rozszerzenia jest **Narzędzia**.

    - **Kategorie**. Wybierz maksymalnie trzy, które najlepiej pasują do Twojego rozszerzenia.

    - **Tagi** są słowami kluczowymi, które pomagają użytkownikom znaleźć Twoje rozszerzenie. Tagi mogą pomóc zwiększyć istotność wyszukiwania rozszerzeń w Visual Studio Marketplace.

    - **Kategoria cennika** to koszt Twojego rozszerzenia.

    - **Repozytorium kodu źródłowego** umożliwia udostępnianie linku do kodu źródłowego społeczności.

    - **Zezwalaj na pytanie,&A dla rozszerzenia** umożliwia użytkownikom pozostawianie pytań na stronie wpisu rozszerzenia.

       \* Nie można zmienić tego podsumowania dla aktualizacji rozszerzenia.

1. Kliknij przycisk **zapisz & Przekaż**. Ta opcja powoduje powrót do strony zarządzania wydawcami. Twoje rozszerzenie nie zostało jeszcze opublikowane.

1. Aby opublikować rozszerzenie, kliknij prawym przyciskiem myszy rozszerzenie i wybierz polecenie **Ustaw jako publiczne**. Aby zobaczyć, jak Twoje rozszerzenie będzie wyglądało Visual Studio Marketplace, wybierz pozycję **Wyświetl rozszerzenie**. W obszarze numery pozyskiwania kliknij pozycję **raporty**. Aby wprowadzić zmiany w rozszerzeniu, kliknij przycisk **Edytuj**.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Dodawanie dodatkowych użytkowników w celu zarządzania kontem wydawcy

Visual Studio Marketplace obsługuje przyznawanie dodatkowych uprawnień użytkownikom do uzyskiwania dostępu do konta wydawcy i zarządzania nim.

1. Przejdź do konta wydawcy, do którego chcesz dodać kolejnych użytkowników.

2. Wybierz pozycję **Członkowie** i kliknij pozycję **Dodaj**.

   ![Dodaj kolejnego użytkownika](media/add-users.png)

3. Następnie można określić adres e-mail użytkownika, który ma zostać dodany i przyznać właściwy poziom dostępu w obszarze **Wybierz rolę**.  Możesz wybrać z następujących opcji:

   * **Twórca**: użytkownik może publikować rozszerzenia, ale nie może wyświetlać rozszerzeń opublikowanych przez innych użytkowników ani nimi zarządzać.

   * **Czytelnik**: użytkownik może wyświetlać rozszerzenia, ale nie może publikować rozszerzeń ani nimi zarządzać.

   * **Współautor**: użytkownik może publikować rozszerzenia i zarządzać nimi, ale nie może edytować ustawień wydawcy ani zarządzać dostępem.

   * **Właściciel**: użytkownik może publikować rozszerzenia i zarządzać nimi, edytować ustawienia wydawcy i zarządzać dostępem.

## <a name="install-the-extension-from-visual-studio-marketplace"></a>Zainstaluj rozszerzenie z Visual Studio Marketplace

Po opublikowaniu rozszerzenia zainstaluj je w programie Visual Studio i przetestuj je w tym miejscu.

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **rozszerzenia i aktualizacje**.

2. Kliknij pozycję **online** , a następnie wyszukaj ciąg **TestPublish**.

3. Kliknij pozycję **Pobierz**. To rozszerzenie jest zaplanowane do instalacji.

4. Aby ukończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuwanie rozszerzenia

Można usunąć rozszerzenie z Visual Studio Marketplace i z komputera.

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>Aby usunąć rozszerzenie z Visual Studio Marketplace

1. Przejdź do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. W prawym górnym rogu kliknij pozycję **Publikuj** rozszerzenia. Wybierz wydawcę, który został użyty do opublikowania **TestPublish**. Zostanie wyświetlona lista dla **TestPublish** .

3. Kliknij prawym przyciskiem myszy wpis rozszerzenia i kliknij polecenie **Usuń**. Zostanie wyświetlony monit o potwierdzenie, czy chcesz usunąć rozszerzenie. Kliknij przycisk **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenie z komputera

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **rozszerzenia i aktualizacje**.

2. Wybierz pozycję **TestPublish** , a następnie kliknij pozycję **Odinstaluj**. Rozszerzenie jest następnie zaplanowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
