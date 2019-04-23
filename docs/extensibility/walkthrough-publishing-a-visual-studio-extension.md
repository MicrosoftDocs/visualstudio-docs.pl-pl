---
title: 'Przewodnik: Publikowanie rozszerzenia programu Visual Studio | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a7bf7d49430923652ece66fc566ee75af1884d0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093353"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Przewodnik: Publikowanie rozszerzenia programu Visual Studio

W tym instruktażu dowiesz się, jak opublikować rozszerzenia programu Visual Studio do witryny Marketplace programu Visual Studio. Po dodaniu rozszerzenia w portalu Marketplace, deweloperzy mogą używać **rozszerzenia i aktualizacje** Aby przeglądać w poszukiwaniu nowych i zaktualizowanych rozszerzenia.

## <a name="prerequisites"></a>Wymagania wstępne

 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Tworzenie rozszerzenia programu Visual Studio

W tym artykule użyto rozszerzenia pakietu VSPackage domyślnego, ale kroki są prawidłowe dla każdego rodzaju rozszerzenia.

1. Tworzenie pakietu VSPackage w języku C# o nazwie `TestPublish` zawierający polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie pierwszego rozszerzenia: Witaj, świecie](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Pakiet rozszerzenia

1. Zaktualizuj rozszerzenie *.vsixmanifest* poprawne informacje na temat nazwy produktu, autora i wersji.

   ![Aktualizacja rozszerzenia vsixmanifest](media/update-extension-vsixmanifest.png)

2. Tworzenie rozszerzenia w **wersji** trybu. Teraz rozszerzenie jest ona dostępna jako pakiet VSIX w folderze \bin\Release.

3. Możesz kliknąć dwukrotnie VSIX, aby zweryfikować instalację.

## <a name="test-the-extension"></a>Testowanie rozszerzenia

 Przed rozpoczęciem dystrybucji rozszerzenia, twórz i go przetestować, aby upewnić się, że jest poprawnie zainstalowane w doświadczalnym wystąpieniu programu Visual Studio.

1. W programie Visual Studio rozpocząć debugowanie, aby otworzyć doświadczalne wystąpienie programu Visual Studio.

2. W doświadczalnym wystąpieniu, przejdź do **narzędzia** menu i kliknij przycisk **rozszerzenia i aktualizacje**. Rozszerzenie TestPublish powinna zostać wyświetlona w środkowym okienku i włączone.

3. Na **narzędzia** menu, upewnij się, zobacz polecenia testowania.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publikowanie rozszerzenia do witryny Marketplace programu Visual Studio

1. Upewnij się, czy został wcześniej utworzony wersji rozszerzenia i że jest on aktualny.

2. Otwórz w przeglądarce sieci web [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) witryny sieci Web.

3. W prawym górnym rogu kliknij **Zaloguj**.

4. Użyj konta Microsoft do logowania. Jeśli nie masz konta Microsoft, możesz go utworzyć w tym momencie.

5. Kliknij przycisk **publikowania rozszerzenia**.  Ta opcja powoduje przejście do strony zarządzania dla wszystkich rozszerzeń. Jeśli nie masz konta wydawcy są zostanie wyświetlony monit, aby je utworzyć w tej chwili.

   ![Przekaż do witryny Marketplace](media/upload-to-marketplace.png)

6. Wybierz wydawcę, którego chcesz użyć, aby przekazać Twoje rozszerzenie. Możesz zmienić wydawcy, klikając na liście po lewej stronie nazwy wydawcy. Kliknij pozycję **nowe rozszerzenie** i wybierz **programu Visual Studio**.

7. W **1: Przekazywanie rozszerzenia**, możesz przekazać plik VSIX bezpośrednio do programu Visual Studio Marketplace lub po prostu Dodaj link do własnej witryny sieci Web. W tym przykładzie rozszerzenie *TestPublish.vsix* zostanie przekazany. Przeciągnij i upuść Twojego rozszerzenia lub użyj **kliknij** link, aby przejść do pliku. Znajdź rozszerzenia w folderze \bin\Release projektu.  Kliknij przycisk **Kontynuuj**.

8. W **2: Podaj szczegóły rozszerzenia**, niektóre pola są wypełniane automatycznie z *source.extension.vsixmanifest* plik z Twojego rozszerzenia. Znajdź więcej szczegółów dotyczących poszczególnych poniżej:

    * **Nazwa wewnętrzna** jest używana w adresie URL strony szczegółów rozszerzenia. Na przykład publikowania rozszerzenia w obszarze nazwy wydawcy "MojaNazwa" i określanie nazw wewnętrznych do "Moje rozszerzenie" wyniki w adresie URL "marketplace.visualstudio\.com/items?itemName=myname.myextension" Szczegóły Twojego rozszerzenia Strona.

    * **Nazwa wyświetlana** Twojego rozszerzenia. Ta nazwa jest automatycznie wypełnione z *source.extension.vsixmanifest* pliku.

    * **Wersja** liczba rozszerzenia przekazywania. Ta wersja jest wypełniany automatycznie z *source.extension.vsixmanifest* pliku.

    * **Identyfikator VSIX** jest unikatowy identyfikator, który korzysta z programu Visual Studio dla rozszerzenia. Ten identyfikator jest wymagany, jeśli chcesz mieć rozszerzenie automatycznie aktualizowane. Ten identyfikator jest wypełniany automatycznie z *source.extension.vsixmanifest* pliku.

    * **Logo** używany dla rozszerzenia. Jest wypełniany automatycznie z *source.extension.vsixmanifest* pliku Jeśli podano.

    * **Krótki opis** funkcji co Twoje rozszerzenie. Ten opis jest wypełniany automatycznie z *source.extension.vsixmanifest* pliku.

    * **Omówienie** jest dobrym miejscem do uwzględnienia zrzutów ekranu i szczegółowe informacje na temat działania Twojego rozszerzenia.

    * **Obsługiwane wersje programu Visual Studio** pozwala wybrać, które wersje programu Visual Studio rozszerzenie będzie działać na. Rozszerzenie jest ona instalowana tylko do tych wersji.

    * ** Obsługiwane edition pozwala na wybór jakie wersje programu Visual Studio rozszerzenie będzie działać na z programu Visual Studio. Rozszerzenie jest ona instalowana tylko do tych wersji.

    * **Typ**. Najczęściej spotykanym typem rozszerzenia są **narzędzia**.

    * **Kategorie**. Wybierz maksymalnie trzy, które są najlepszym rozwiązaniem dla rozszerzenia.

    * **Tagi** są słowa kluczowe, które ułatwiają użytkownikom znajdowanie Twojego rozszerzenia. Tagi mogą pomóc w zwiększeniu trafności wyszukiwania rozszerzeń w portalu Marketplace.

    * **Cennik kategorii** jest koszt Twojego rozszerzenia.

    * **Repozytorium kodu źródłowego** umożliwia udostępnianie linku do kodu źródłowego ze społecznością.

    * **Zezwalaj na pytania i odpowiedzi dla rozszerzenia** pozwala użytkownikom na stronie wpis rozszerzenia należy pozostawić pytania.

9. Kliknij przycisk **Zapisz prze & kazywanie**. Strona Zarządzanie tym wymaga opcji, możesz z powrotem do wydawcy. Rozszerzenia nie został jeszcze opublikowany. Aby opublikować Twojego rozszerzenia, kliknij prawym przyciskiem myszy na Twoje rozszerzenie i wybierz **Upublicznij**. Można wyświetlić, jak rozszerzenie będzie wyglądało w portalu Marketplace, wybierając **rozszerzenie widoku**. W przypadku nabycia liczb, kliknij pozycję **raporty**. Aby wprowadzić zmiany do rozszerzenia, wybierz polecenie **Edytuj**.

   ![Rozszerzenie wpis Menu](media/extension-entry-menu.png)

10. Po kliknięciu przycisku **Upublicznij**, rozszerzenia jest obecnie dostępna publicznie. Wyszukaj Visual Studio Marketplace dla rozszerzenia.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Aby dodać kolejnych użytkowników, Zarządzanie kontem wydawcy

Portal Marketplace obsługuje udzielanie użytkownikom dodatkowe uprawnienia do dostępu i zarządzania konta wydawcy.

1. Przejdź do konta wydawcy, który chcesz dodać dodatkowym użytkownikom.

2. Wybierz **członków** i kliknij pozycję **Dodaj**.

   ![Dodawanie dodatkowych użytkowników](media/add-users.png)

3. Następnie możesz określić adres e-mail użytkownika, o których chcesz dodać, a następnie przyznać odpowiedni poziom dostępu w ramach **wybierz rolę**.  Można wybrać następujące opcje:

   * **Twórca**: Użytkownika można publikować rozszerzenia, ale nie można wyświetlić lub zarządzać rozszerzenia publikowane przez innych użytkowników.

   * **Czytnik**: Użytkownika można wyświetlanie tych rozszerzeń, ale nie można publikować lub Zarządzaj rozszerzeniami.

   * **Współautor**: Użytkownika można publikować i zarządzania rozszerzeniami, ale nie można edytować ustawienia wydawcy lub zarządzania dostępem.

   * **Właściciel**: Użytkownik może opublikować Zarządzaj rozszerzeniami, edytować ustawienia wydawcy i zarządzanie dostępem do.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Należy zainstalować rozszerzenie z witryny Marketplace programu Visual Studio

Teraz, gdy rozszerzenie zostanie opublikowany, zainstaluj go w programie Visual Studio i przetestować.

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

2. Kliknij przycisk **Online** a następnie wyszukaj **TestPublish**.

3. Kliknij przycisk **Pobierz**. Rozszerzenie następnie jest zaplanowane do instalacji.

4. Aby ukończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuń rozszerzenie

Można usunąć rozszerzenie z witryny Marketplace programu Visual Studio i z tego komputera.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Aby usunąć rozszerzenie z witryny Marketplace programu Visual Studio

1. Otwórz [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) witryny sieci Web.

2. W prawym górnym rogu kliknij **Publikuj** rozszerzenia. Wybierz wydawcy, który umożliwia publikowanie **TestPublish**. Listę **TestPublish** pojawia się.

3. Kliknij prawym przyciskiem myszy wpis rozszerzenia, a następnie kliknij przycisk **Usuń**. Zostanie wyświetlony monit o potwierdzenie, jeśli chcesz usunąć rozszerzenie. Kliknij przycisk **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenie z komputera

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

2. Wybierz **TestPublish** a następnie kliknij przycisk **Odinstaluj**. Rozszerzenie następnie jest zaplanowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
