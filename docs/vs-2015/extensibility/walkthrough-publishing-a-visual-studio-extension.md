---
title: Publikowanie rozszerzenia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27a581175fd0cb63a598006ea2519058bdd8fcbe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781518"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Przewodnik: Publikowanie rozszerzenia programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Uwaga**: W galerii Visual Studio jest zastępowany przez Visual Studio Marketplace. Zobaczyć najnowszą wersję tego tematu, aby uzyskać szczegółowe informacje.


W tym instruktażu dowiesz się, jak opublikować rozszerzenia programu Visual Studio do galerii Visual Studio. Po dodaniu rozszerzenia w galerii, deweloperzy mogą używać **rozszerzenia i aktualizacje** przeglądać dostępne dla nowych i zaktualizowanych rozszerzeń.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Tworzenie rozszerzenia programu Visual Studio
 W tym przypadku użyjemy rozszerzenia pakietu VSPackage domyślnego, ale te same kroki są prawidłowe dla każdego rodzaju rozszerzenia.

1.  Tworzenie pakietu VSPackage w języku C# o nazwie `TestPublishing` zawierający polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Testowanie rozszerzenia
 Przed rozpoczęciem dystrybucji rozszerzenia, twórz i go przetestować, aby upewnić się, że jest poprawnie zainstalowane w doświadczalnym wystąpieniu programu Visual Studio.

1.  W programie Visual Studio Rozpocznij debugowanie. Aby otworzyć doświadczalne wystąpienie programu Visual Studio.

2.  W doświadczalnym wystąpieniu, przejdź do **narzędzia** menu i kliknij przycisk **Menedżera rozszerzeń**. Rozszerzenie TestPublishing powinna zostać wyświetlona w środkowym okienku i włączone.

3.  Na **narzędzia** menu, upewnij się, zobacz polecenia testowania.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publikowanie rozszerzenia do galerii Visual Studio
 Teraz możesz opublikować rozszerzenie do galerii Visual Studio.

1.  Upewnij się, czy został wcześniej utworzony wersji rozszerzenia i że jest on aktualny.

2.  Otwórz w przeglądarce sieci web [galerii Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) witryny sieci Web.

3.  W prawym górnym rogu kliknij **SIGN IN**.

4.  Użyj konta Microsoft do logowania. Jeśli nie masz konta Microsoft, możesz go utworzyć w tym momencie.

5.  Kliknij pozycję **Przekaż**.

6.  W **krok 1: Typ rozszerzenia**, wybierz opcję **narzędzie** a następnie kliknij przycisk **dalej**.

7.  W **krok 2: Przekaż**, można przekazać bezpośrednio do galerii Visual Studio, albo po prostu Dodaj link do własnej witryny sieci Web. W takim przypadku wybierz **chcę przekazać moje narzędzie**. **Wybrać kontrolkę** pojawi się okno. Kliknij przycisk **Przeglądaj** a następnie wybierz TestPublish.vsix w folderze \bin\Release projektu. Kliknij przycisk **Dalej**.

8.  W **krok 3: Podstawowe informacje**, pola z pliku source.extension.vsixmanifest są wyświetlane. Wybierz odpowiednią **kategorii** i Dodaj **tagi** na ułatwienie użytkownikom znalezienia Twojego rozszerzenia. Można dodać bardziej szczegółowe podsumowanie i opis (opis musi składać się przynajmniej 280 znaków). Pozostaw **typ rozszerzenia** jako **nie rozszerzenie Microsoft** i **kategorii kosztu** jako **wersji próbnej**.

9. Przeczytaj Umowa dotycząca materiałów przekazywanych w dolnej części strony i sprawdź **zgodę**.

10. Kliknij przycisk **Utwórz wkład**. Spowoduje to wyświetlenie strony, posiadane swoje rozszerzenie w galerii Visual Studio, wyświetleniem komunikatu informującego o tym, że strona nie została jeszcze opublikowana.

11. Kliknij przycisk **publikowania**.

12. Wyszukiwanie w galerii Visual Studio dla rozszerzenia. Powinna zostać wyświetlona lista rozszerzenia TestPublish.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Instalowanie rozszerzenia z galerii Visual Studio
 Teraz, gdy rozszerzenie zostanie opublikowany, zainstaluj go w programie Visual Studio i przetestować.

1.  W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

2.  Kliknij przycisk **Online** a następnie wyszukaj TestPublish. Powinna zostać wyświetlona lista rozszerzenia TestPublish.

3.  Kliknij przycisk **Pobierz**. Po pobraniu rozszerzenia kliknij **zainstalować**.

4.  Aby ukończyć instalację, uruchom ponownie program Visual Studio.

## <a name="removing-the-extension"></a>Usuwanie rozszerzenia
 Można usunąć rozszerzenia z galerii Visual Studio i z tego komputera.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Można usunąć rozszerzenia z galerii Visual Studio

1.  Otwórz [galerii Visual Studio](http://go.microsoft.com/fwlink/?LinkId=194329) witryny sieci Web.

2.  W prawym górnym rogu kliknij **Moje Extenions**. Listę TestPublish jest wyświetlany.

3.  Kliknij przycisk **Usuń**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenie z komputera

1.  W programie Visual Studio na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzeń**.

2.  Wybierz TestPublish, a następnie kliknij przycisk **Odinstaluj**.

3.  Aby ukończyć dezinstalację, uruchom ponownie program Visual Studio.
