---
title: 'Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++ | Microsoft Docs'
description: Dowiedz się, jak utworzyć natywny zestaw SDK biblioteki matematycznej języka C++, spakować zestaw SDK jako rozszerzenie programu Visual Studio, a następnie użyć go do utworzenia aplikacji za pomocą tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d4baeb8a93a1bb5e70f3ee6266bb1a832a2a3fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080414"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++
W tym instruktażu pokazano, jak utworzyć natywny zestaw SDK biblioteki matematycznej języka C++, spakować zestaw SDK jako rozszerzenie programu Visual Studio (VSIX), a następnie użyć go do utworzenia aplikacji. Przewodnik jest podzielony na następujące kroki:

- [Aby utworzyć biblioteki natywne i środowisko wykonawcze systemu Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Aby utworzyć projekt rozszerzenia NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Aby utworzyć biblioteki natywne i środowisko wykonawcze systemu Windows

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. Na liście szablonów rozwiń węzeł **Visual C++**  >  **uniwersalnym systemu Windows**, a następnie wybierz szablon **dll (Aplikacje uniwersalne systemu Windows)** . W polu **Nazwa** Określ `NativeMath` , a następnie wybierz przycisk **OK** .

3. Zaktualizuj *NativeMath. h* , aby pasował do poniższego kodu.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Zaktualizuj *NativeMath. cpp* , aby dopasować ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. W **Eksplorator rozwiązań** Otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz polecenie **Dodaj**  >  **Nowy projekt**.

6. Na liście szablonów rozwiń węzeł **Visual C++**, a następnie wybierz szablon **środowisko wykonawcze systemu Windows składnika** . W polu **Nazwa** Określ `NativeMathWRT` , a następnie wybierz przycisk **OK** .

7. Zaktualizuj *Class1. h* , aby dopasować ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Zaktualizuj *Class1. cpp* , aby dopasować ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Aby utworzyć projekt rozszerzenia NativeMathVSIX

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz polecenie **Dodaj**  >  **Nowy projekt**.

2. Na liście szablonów rozwiń węzeł rozszerzalność **języka Visual C#**  >  , a następnie wybierz pozycję **Projekt VSIX**. W polu **Nazwa** Określ **NativeMathVSIX**, a następnie wybierz przycisk **OK** .

3. W **Eksplorator rozwiązań** Otwórz menu skrótów dla elementu **source. Extension. vsixmanifest**, a następnie wybierz polecenie **Wyświetl kod**.

4. Użyj poniższego kodu XML, aby zastąpić istniejący kod XML.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **NativeMathVSIX** , a następnie wybierz polecenie **Dodaj**  >  **nowy element**.

6. Na liście **elementów języka Visual C#** rozwiń pozycję **dane**, a następnie wybierz pozycję **plik XML**. W polu **Nazwa** Określ `SDKManifest.xml` , a następnie wybierz przycisk **OK** .

7. Użyj tego kodu XML, aby zastąpić zawartość pliku:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. W **Eksplorator rozwiązań** w projekcie **NativeMathVSIX** Utwórz tę strukturę folderów:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. W **Eksplorator rozwiązań** Otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.

10. W **Eksploratorze plików** Skopiuj *$SolutionRoot $ \NativeMath\NativeMath.h*, a następnie w **Eksplorator rozwiązań**, w projekcie **NativeMathVSIX** , wklej go w folderze *$SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include \\* .

     Skopiuj *$SolutionRoot $ \Debug\NativeMath\NativeMath.lib*, a następnie wklej go w folderze *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* .

     Skopiuj *$SolutionRoot $\Debug\NativeMath\NativeMath.dll* i wklej go w folderze *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86 \\* .

     Skopiuj *$SolutionRoot $\Debug\NativeMathWRT\NativeMathWRT.dll* i wklej go w folderze *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* .
     Skopiuj *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.winmd* i wklej go w folderze *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

     Skopiuj *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.pri* i wklej go w folderze *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

11. W folderze *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* Utwórz plik tekstowy o nazwie *NativeMathSDK. props*, a następnie wklej w nim następującą zawartość:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Na pasku menu wybierz **Widok**  >  **inne**  >  **Właściwości okna** (klawiatura: wybierz klawisz **F4** ).

13. W obszarze **Eksplorator rozwiązań** wybierz plik **NativeMathWRT. winmd** . W oknie **Właściwości** Zmień właściwość **Akcja kompilacji** na **zawartość**, a następnie zmień wartość właściwości **Dołącz w VSIX** na **true**.

     Powtórz ten proces dla pliku **NativeMath. h** .

     Powtórz ten proces dla pliku **NativeMathWRT. pri** .

     Powtórz ten proces dla pliku **NativeMath. lib** .

     Powtórz ten proces dla pliku **NativeMathSDK. props** .

14. W **Eksplorator rozwiązań** wybierz plik **NativeMath. h** . W oknie **Właściwości** Zmień wartość właściwości **Dołącz w VSIX** na **true**.

     Powtórz ten proces dla pliku **NativeMath.dll** .

     Powtórz ten proces dla pliku **NativeMathWRT.dll** .

     Powtórz ten proces dla pliku **SDKManifest.xml** .

15. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

16. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **NativeMathVSIX** , a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.

17. W **Eksploratorze plików** przejdź do folderu *$SolutionRoot $ \NativeMathVSIX\bin\Debug* , a następnie uruchom plik *NativeMathVSIX. vsix* , aby rozpocząć instalację.

18. Wybierz przycisk **Zainstaluj** , poczekaj na zakończenie instalacji, a następnie otwórz program Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Aby utworzyć przykładową aplikację, która używa biblioteki klas

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. Na liście szablonów rozwiń węzeł **Visual C++**  >  **uniwersalnym systemu Windows** , a następnie wybierz pozycję **pusta aplikacja**. W polu **Nazwa** Określ **NativeMathSDKSample**, a następnie wybierz przycisk **OK** .

3. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **NativeMathSDKSample** , a następnie wybierz **Dodaj**  >  **odwołanie**.

4. W oknie dialogowym **Dodaj odwołanie** na liście typów referencyjnych rozwiń węzeł **uniwersalne okna**, a następnie wybierz pozycję **rozszerzenia**. Na koniec zaznacz pole wyboru **natywny zestaw SDK matematycznych** , a następnie wybierz przycisk **OK** .

5. Wyświetl właściwości projektu dla NativeMathSDKSample.

    Właściwości zdefiniowane w *NativeMathSDK. props* zostały zastosowane po dodaniu odwołania. Można sprawdzić, czy właściwości zostały zastosowane, sprawdzając Właściwość **katalogów VC + +** **Właściwości konfiguracji** projektu.

6. W **Eksplorator rozwiązań** Otwórz **MainPage. XAML**, a następnie użyj następującego języka XAML, aby zastąpić jego zawartość:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Zaktualizuj *MainPage. XAML. h* , aby dopasować ten kod:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Zaktualizuj *MainPage. XAML. cpp* , aby dopasować ten kod:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Wybierz klawisz **F5** , aby uruchomić aplikację.

10. W aplikacji wprowadź dwie liczby, wybierz operację, a następnie wybierz **=** przycisk.

     Zostanie wyświetlony prawidłowy wynik.

    W tym instruktażu pokazano, jak utworzyć zestaw SDK rozszerzenia i użyć go do wywołania [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteki i innej niż [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] Biblioteka.

## <a name="next-steps"></a>Następne kroki

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Tworzenie zestawu SDK przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
