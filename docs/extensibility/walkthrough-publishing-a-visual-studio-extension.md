---
title: 'Przewodnik: Publikowanie rozszerzenia programu Visual Studio | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697142"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Instruktaż: publikowanie rozszerzenia programu Visual Studio

W tym przewodniku pokazano, jak opublikować rozszerzenie programu Visual Studio w portalu Visual Studio Marketplace. Po dodaniu rozszerzenia do portalu Marketplace deweloperzy mogą używać **rozszerzeń i aktualizacji** do przeglądania nowych i zaktualizowanych rozszerzeń.

## <a name="prerequisites"></a>Wymagania wstępne

 Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Tworzenie rozszerzenia programu Visual Studio

W tym artykule użyto domyślnego rozszerzenia VSPackage, ale kroki są prawidłowe dla każdego rodzaju rozszerzenia.

1. Utwórz pakiet VSPackage `TestPublish` w języku C# o nazwie, która ma polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie pierwszego rozszerzenia: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Pakiet rozszerzenia

1. Zaktualizuj rozszerzenie *.vsixmanifest* o poprawne informacje o nazwie produktu, autorze i wersji.

   ![rozszerzenie aktualizacji vsixmanifest](media/update-extension-vsixmanifest.png)

2. Tworzenie rozszerzenia w trybie **wydania.** Teraz rozszerzenie jest pakowane jako VSIX w folderze \bin\Release.

3. Można kliknąć dwukrotnie VSIX, aby zweryfikować instalację.

## <a name="test-the-extension"></a>Testowanie rozszerzenia

 Przed dystrybucją rozszerzenia, skompilować i przetestować go, aby upewnić się, że jest poprawnie zainstalowany w eksperymentalnym wystąpieniu programu Visual Studio.

1. W programie Visual Studio uruchom debugowanie, aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

2. W przypadku wystąpienia eksperymentalnego przejdź do menu **Narzędzia** i kliknij polecenie **Rozszerzenia i aktualizacje**. Rozszerzenie TestPublish powinno pojawić się w środkowym okienku i być włączone.

3. W menu **Narzędzia** upewnij się, że jest widoczne polecenie testu.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publikowanie rozszerzenia w portalu Visual Studio Marketplace

1. Upewnij się, że została skonstowana wersja wersji rozszerzenia i że jest aktualna.

2. W przeglądarce sieci Web otwórz witrynę sieci Web [w witrynie portalu Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

3. W prawym górnym rogu kliknij pozycję **Zaloguj**się .

4. Zaloguj się za pomocą konta Microsoft. Jeśli nie masz konta Microsoft, możesz je utworzyć w tym momencie.

5. Kliknij pozycję **Publikuj rozszerzenia**.  Ta opcja przechodzi do strony zarządzania dla wszystkich rozszerzeń. Jeśli nie masz konta wydawcy, zostanie wyświetlony monit o jego utworzenie w tej chwili.

   ![Prześlij do Marketplace](media/upload-to-marketplace.png)

6. Wybierz wydawcę, którego chcesz użyć do przesłania rozszerzenia. Wydawców możesz zmienić, klikając nazwy wydawców wymienione po lewej stronie. Kliknij **nowe rozszerzenie** i wybierz program **Visual Studio**.

7. W **1: Rozszerzenie przekazywania**, można przesłać plik VSIX bezpośrednio do programu Visual Studio Marketplace lub po prostu dodać link do własnej witryny sieci Web. W tym przykładzie rozszerzenie *TestPublish.vsix* jest przekazywał. Przeciągnij i upuść rozszerzenie lub użyj łącza **kliknięcia,** aby wyszukać plik. Znajdź rozszerzenie w folderze \bin\Release projektu.  Kliknij przycisk **Kontynuuj**.

8. W **2: Podaj szczegóły rozszerzenia,** niektóre pola są automatycznie wypełniane z pliku *source.extension.vsixmanifest* z rozszerzenia. Dowiedz się więcej o każdym z nich poniżej:

    * **Nazwa wewnętrzna** jest używana w adresie URL strony szczegółów rozszerzenia. Na przykład opublikowanie rozszerzenia pod nazwą wydawcy "myname" i określenie nazwy wewnętrznej jako "moje rozszerzenie" powoduje\.wyświetlenie adresu URL "marketplace.visualstudio com/items?itemName=myname.myextension" dla strony szczegółów rozszerzenia.

    * **Wyświetl nazwę** rozszerzenia. Ta nazwa jest automatycznie wypełniana z pliku *source.extension.vsixmanifest.*

    * Numer **wersji** przesłanego rozszerzenia. Ta wersja jest automatycznie wypełniona z pliku *source.extension.vsixmanifest.*

    * **IDENTYFIKATOR VSIX** to unikatowy identyfikator używany przez program Visual Studio dla rozszerzenia. Ten identyfikator jest wymagany, jeśli chcesz, aby rozszerzenie było automatycznie aktualizowane. Ten identyfikator jest automatycznie wypełniany z pliku *source.extension.vsixmanifest.*

    * **Logo** używane do rozszerzenia. To logo jest automatycznie wypełniane z pliku *source.extension.vsixmanifest,* jeśli jest pod warunkiem.

    * **Krótki opis** tego, co robi rozszerzenie. Ten opis jest automatycznie wypełniany z pliku *source.extension.vsixmanifest.*

    * **Przegląd** jest dobrym miejscem do dołączania zrzutów ekranu i szczegółowych informacji o tym, co robi rozszerzenie.

    * **Obsługiwane wersje programu Visual Studio** pozwala wybrać, które wersje programu Visual Studio rozszerzenie będzie działać na. Rozszerzenie jest zainstalowane tylko w tych wersjach.

    * **Obsługiwana wersja programu Visual Studio pozwala wybrać, które wersje programu Visual Studio będzie działać nad rozszerzeniem. Twoje rozszerzenie jest zainstalowane tylko w tych wersjach.

    * **Wpisz**. Najczęstszym typem rozszerzeń są **narzędzia**.

    * **Kategorie**. Wybierz do trzech, które najlepiej pasują do twojego rozszerzenia.

    * **Tagi** to słowa kluczowe, które pomagają użytkownikom znaleźć twoje rozszerzenie. Tagi mogą zwiększyć trafność wyszukiwania rozszerzeń w Portalu Marketplace.

    * **Kategoria cen** to koszt rozszerzenia.

    * **Repozytorium kodu źródłowego** umożliwia udostępnianie łącza do kodu źródłowego społeczności.

    * **Zezwalaj na Q&A dla rozszerzenia,** dzięki temu użytkownicy mogą zostawiać pytania na stronie wprowadzania rozszerzenia.

9. Kliknij **pozycję Zapisz & przekaż**. Ta opcja spowoduje powrót do strony zarządzania wydawcą. Twoje rozszerzenie nie zostało jeszcze opublikowane. Aby opublikować rozszerzenie, kliknij prawym przyciskiem myszy rozszerzenie i wybierz pozycję **Udostępnij publicznie**. Możesz zobaczyć, jak rozszerzenie będzie wyglądać w Marketplace, wybierając **opcję Wyświetl rozszerzenie**. W przypadku numerów nabycia kliknij pozycję **Raporty**. Aby wprowadzić zmiany w rozszerzeniu, kliknij **edytuj**.

   ![Menu wpisu rozszerzenia](media/extension-entry-menu.png)

10. Po kliknięciu przycisku **Udostępnij publicznie**rozszerzenie jest teraz publiczne. Przeszukaj w witrynie Visual Studio Marketplace w poszukiwaniu rozszerzenia.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Dodawanie dodatkowych użytkowników do zarządzania kontem wydawcy

Marketplace obsługuje przyznawanie dodatkowych uprawnień użytkowników do uzyskiwania dostępu do konta wydawcy i zarządzania nim.

1. Przejdź do konta wydawcy, do którego chcesz dodać dodatkowych użytkowników.

2. Wybierz **członków** i kliknij **dodaj**.

   ![Dodaj dodatkowego użytkownika](media/add-users.png)

3. Następnie można określić adres e-mail użytkownika, którego chcesz dodać, i udzielić odpowiedniego poziomu dostępu w obszarze **Wybierz rolę**.  Możesz wybrać z następujących opcji:

   * **Twórca**: Użytkownik może publikować rozszerzenia, ale nie może wyświetlać rozszerzeń publikowanych przez innych użytkowników ani zarządzać nimi.

   * **Czytnik:** Użytkownik może wyświetlać rozszerzenia, ale nie może publikować rozszerzeń ani nimi zarządzać.

   * **Współautor:** Użytkownik może publikować rozszerzenia i zarządzać nimi, ale nie może edytować ustawień wydawcy ani zarządzać dostępem.

   * **Właściciel**: Użytkownik może publikować rozszerzenia i zarządzać nimi, edytować ustawienia wydawcy i zarządzać dostępem.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instalowanie rozszerzenia z portalu Visual Studio Marketplace

Teraz, gdy rozszerzenie zostanie opublikowane, zainstaluj je w programie Visual Studio i przetestuj je tam.

1. W programie Visual Studio w menu **Narzędzia** kliknij polecenie **Rozszerzenia i aktualizacje**.

2. Kliknij **pozycję Online,** a następnie wyszukaj **pozycję TestPublish**.

3. Kliknij **pozycję Pobierz**. Rozszerzenie jest następnie zaplanowane do zainstalowania.

4. Aby zakończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuwanie rozszerzenia

Rozszerzenie można usunąć z witryny Visual Studio Marketplace i z komputera.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Aby usunąć rozszerzenie z portalu Visual Studio Marketplace

1. Otwórz witrynę sieci Web [programu Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

2. W prawym górnym rogu kliknij pozycję **Publikuj** rozszerzenia. Wybierz wydawcę użytego do opublikowania **programu TestPublish**. Zostanie wyświetlena lista **dla aplikacji TestPublish.**

3. Kliknij prawym przyciskiem myszy wpis rozszerzenia i kliknij polecenie **Usuń**. Zostaniesz poproszony o potwierdzenie, czy chcesz usunąć rozszerzenie. Kliknij przycisk **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenie z komputera

1. W programie Visual Studio w menu **Narzędzia** kliknij polecenie **Rozszerzenia i aktualizacje**.

2. Wybierz **pozycję TestPublish,** a następnie kliknij pozycję **Odinstaluj**. Rozszerzenie jest następnie zaplanowane do odinstalowania.

3. Aby zakończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
