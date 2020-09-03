---
title: Publikowanie rozszerzenia | Microsoft Docs
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
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201968"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Przewodnik: publikowanie rozszerzenia programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Uwaga**: Galeria programu Visual Studio jest zastępowana przez Visual Studio Marketplace. Zobacz najnowszą wersję tego tematu, aby uzyskać szczegółowe informacje.

W tym instruktażu pokazano, jak opublikować rozszerzenie programu Visual Studio w galerii programu Visual Studio. Po dodaniu rozszerzenia do galerii deweloperzy mogą użyć **rozszerzeń i aktualizacji** , aby przeglądać w poszukiwaniu nowych i zaktualizowanych rozszerzeń.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Utwórz rozszerzenie programu Visual Studio
 W takim przypadku użyjemy domyślnego rozszerzenia pakietu VSPackage, ale te same kroki są prawidłowe dla każdego rodzaju rozszerzenia.

1. Utwórz element pakietu VSPackage w języku C# o nazwie `TestPublishing` , który ma polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Testowanie rozszerzenia
 Przed rozpoczęciem dystrybucji rozszerzenia Skompiluj i przetestuj je, aby upewnić się, że jest poprawnie zainstalowana w eksperymentalnym wystąpieniu programu Visual Studio.

1. W programie Visual Studio Rozpocznij debugowanie. , aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

2. W eksperymentalnym wystąpieniu przejdź do menu **Narzędzia** , a następnie kliknij pozycję **Menedżer rozszerzeń**. Rozszerzenie TestPublishing powinno pojawić się w środkowym okienku i być włączone.

3. W menu **Narzędzia** upewnij się, że widzisz polecenie Test.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Publikowanie rozszerzenia w galerii programu Visual Studio
 Teraz można opublikować rozszerzenie w galerii programu Visual Studio.

1. Upewnij się, że masz wbudowaną wersję wydania rozszerzenia oraz że jest ona aktualna.

2. W przeglądarce sieci Web otwórz witrynę [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

3. W prawym górnym rogu kliknij pozycję **Zaloguj się**.

4. Zaloguj się przy użyciu konto Microsoft. Jeśli nie masz konto Microsoft, możesz go utworzyć w tym momencie.

5. Kliknij pozycję **Przekaż**.

6. W **kroku 1: typ rozszerzenia**, wybierz **Narzędzie** , a następnie kliknij przycisk **dalej**.

7. W **kroku 2: przekazywanie**możesz przekazać bezpośrednio do galerii Visual Studio lub po prostu dodać link do własnej witryny sieci Web. W tym przypadku wybierz opcję **chcę przekazać moje narzędzie**. Zostanie wyświetlone okno **Wybierz kontrolkę** . Kliknij przycisk **Przeglądaj** , a następnie wybierz pozycję TestPublish. vsix w folderze \bin\Release projektu. Kliknij przycisk **Dalej**.

8. W **kroku 3: informacje podstawowe**, pola z pliku source. Extension. vsixmanifest są wyświetlane. Wybierz odpowiednią **kategorię** i Dodaj **Tagi** , aby ułatwić użytkownikom znalezienie rozszerzenia. Możesz chcieć dodać bardziej szczegółowe podsumowanie i opis (opis musi składać się z co najmniej 280 znaków). Pozostaw **Typ rozszerzenia** jako **inny niż rozszerzenie firmy Microsoft** i **kategorię kosztów** jako **wersję próbną**.

9. Przeczytaj umowę dotyczącą udziałów w dolnej części strony i sprawdź, czy **zgadzam**się.

10. Kliknij przycisk **Utwórz udział**. Spowoduje to wyświetlenie strony, której rozszerzenie będzie miało w galerii programu Visual Studio, z komunikatem, że strona nie została jeszcze opublikowana.

11. Kliknij przycisk **Opublikuj**.

12. Wyszukaj swoje rozszerzenie w galerii programu Visual Studio. Powinna zostać wyświetlona lista dla rozszerzenia TestPublish.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Instalowanie rozszerzenia z galerii programu Visual Studio
 Po opublikowaniu rozszerzenia zainstaluj je w programie Visual Studio i przetestuj je w tym miejscu.

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **rozszerzenia i aktualizacje**.

2. Kliknij pozycję **online** , a następnie wyszukaj ciąg TestPublish. Powinna zostać wyświetlona lista dla rozszerzenia TestPublish.

3. Kliknij pozycję **Pobierz**. Po pobraniu rozszerzenia kliknij przycisk **Zainstaluj**.

4. Aby ukończyć instalację, uruchom ponownie program Visual Studio.

## <a name="removing-the-extension"></a>Usuwanie rozszerzenia
 Można usunąć rozszerzenie z galerii programu Visual Studio i z komputera.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Aby usunąć rozszerzenie z galerii programu Visual Studio

1. Otwórz witrynę sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

2. W prawym górnym rogu kliknij pozycję **Moje Extenions**. Zostanie wyświetlona lista dla TestPublish.

3. Kliknij polecenie **Usuń**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenie z komputera

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**.

2. Wybierz pozycję TestPublish, a następnie kliknij pozycję **Odinstaluj**.

3. Aby ukończyć dezinstalację, uruchom ponownie program Visual Studio.
