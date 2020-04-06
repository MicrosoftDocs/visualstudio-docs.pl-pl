---
title: 'Przewodnik: Tworzenie sdk przy użyciu języka C++ | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697632"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Instruktaż: Tworzenie sdk przy użyciu języka C++
W tym przewodniku pokazano, jak utworzyć natywną bibliotekę matematyczną C++, spakować zestawu SDK jako rozszerzenie programu Visual Studio (VSIX), a następnie użyć go do utworzenia aplikacji. Instruktaż jest podzielony na następujące kroki:

- [Aby utworzyć natywne biblioteki środowiska wykonawczego systemu Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Aby utworzyć projekt rozszerzenia NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Aby utworzyć przykładową aplikację, która korzysta z biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Aby utworzyć natywne biblioteki środowiska wykonawczego systemu Windows

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

2. Na liście szablonów rozwiń rozwiń pozycję **Visual C++** > **Windows Universal**, a następnie wybierz szablon **biblioteki DLL (aplikacje uniwersalne systemu Windows).** W polu **Nazwa** `NativeMath`określ , a następnie wybierz przycisk **OK.**

3. Zaktualizuj *NativeMath.h,* aby dopasować następujący kod.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Zaktualizuj *NativeMath.cpp,* aby dopasować ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. W **Eksploratorze rozwiązań**otwórz menu skrótów dla **rozwiązania "NativeMath",** a następnie wybierz pozycję **Dodaj** > **nowy projekt**.

6. Na liście szablonów rozwiń węzeł **Visual C++,** a następnie wybierz szablon **składnika środowiska wykonawczego systemu Windows.** W polu **Nazwa** `NativeMathWRT`określ , a następnie wybierz przycisk **OK.**

7. Zaktualizuj *Class1.h,* aby dopasować ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Zaktualizuj *class1.cpp,* aby dopasować ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Na pasku menu wybierz pozycję **Build** > **Build Solution**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Aby utworzyć projekt rozszerzenia NativeMathVSIX

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla **rozwiązania "NativeMath",** a następnie wybierz pozycję **Dodaj** > **nowy projekt**.

2. Na liście szablonów rozwiń rozwiń rozciągliwość **programu Visual C#,** > **Extensibility**a następnie wybierz pozycję **VSIX Project**. W polu **Nazwa** określ **nativemathvsix**, a następnie wybierz przycisk **OK.**

3. W **Eksploratorze rozwiązań**otwórz menu skrótów dla **pliku source.extension.vsixmanifest**, a następnie wybierz polecenie **Wyświetl kod**.

4. Użyj następującego pliku XML, aby zastąpić istniejący kod XML.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **NativeMathVSIX,** a następnie wybierz pozycję **Dodaj** > **nowy element**.

6. Na liście **elementów programu Visual C#** rozwiń węzeł **Dane**, a następnie wybierz pozycję **Plik XML**. W polu **Nazwa** `SDKManifest.xml`określ , a następnie wybierz przycisk **OK.**

7. Użyj tego pliku XML, aby zastąpić zawartość pliku:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. W **Eksploratorze rozwiązań**w ramach projektu **NativeMathVSIX** utwórz tę strukturę folderów:

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

9. W **Eksploratorze rozwiązań**otwórz menu skrótów dla **rozwiązania "NativeMath",** a następnie wybierz pozycję **Otwórz folder w Eksploratorze plików**.

10. W **Eksploratorze plików**skopiuj *$SolutionRoot$\NativeMath\NativeMath.h*, a następnie w **Eksploratorze rozwiązań**w ramach projektu **NativeMathVSIX** wklej go do folderu *\\ $SolutionRoot$\NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include.*

     Skopiuj *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*, a następnie wklej ją w folderze *\\ $SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86.*

     Skopiuj *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* i wklej ją w folderze *\\ $SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*

     Skopiuj *plik $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* i wklej go w folderze *$SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*
     Skopiuj *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* i wklej go w folderze *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

     Skopiuj *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* i wklej go w *folderze $SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

11. W folderze *$SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86\\ * utwórz plik tekstowy o nazwie *NativeMathSDK.props,* a następnie wklej w nim następującą zawartość:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Na pasku menu wybierz polecenie **Wyświetl** > inne**okno właściwości** systemu**Windows** > (klawiatura: wybierz klawisz **F4).**

13. W **Eksploratorze rozwiązań**wybierz plik **NativeMathWRT.winmd.** W oknie Właściwości zmień właściwość **Akcja kompilacji** na **Zawartość,** a następnie zmień właściwość **Properties** **Uwzględnij w vsix** na **True**.

     Powtórz ten proces dla pliku **NativeMath.h.**

     Powtórz ten proces dla pliku **NativeMathWRT.pri.**

     Powtórz ten proces dla pliku **NativeMath.Lib.**

     Powtórz ten proces dla pliku **NativeMathSDK.props.**

14. W **Eksploratorze rozwiązań**wybierz plik **NativeMath.h.** W oknie **Właściwości** zmień właściwość **Uwzględnij w VSIX** na **True**.

     Powtórz ten proces dla pliku **NativeMath.dll.**

     Powtórz ten proces dla pliku **NativeMathWRT.dll.**

     Powtórz ten proces dla pliku **SDKManifest.xml.**

15. Na pasku menu wybierz pozycję **Build** > **Build Solution**.

16. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **NativeMathVSIX,** a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.

17. W **Eksploratorze plików**przejdź do folderu *$SolutionRoot$\NativeMathVSIX\bin\Debug,* a następnie uruchom *plik NativeMathVSIX.vsix,* aby rozpocząć instalację.

18. Wybierz przycisk **Zainstaluj,** poczekaj na zakończenie instalacji, a następnie otwórz program Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Aby utworzyć przykładową aplikację, która korzysta z biblioteki klas

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

2. Na liście szablonów rozwiń rozwiń pozycję **Visual C++** > **Windows Universal,** a następnie wybierz pozycję **Pusta aplikacja**. W polu **Nazwa** określ **nativemathSDKSample**, a następnie wybierz przycisk **OK.**

3. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **NativeMathSDKSample,** a następnie wybierz pozycję **Dodaj** > **odwołanie**.

4. W oknie dialogowym **Dodawanie odwołania** na liście typów odwołań rozwiń węzeł **Uniwersalny system Windows**, a następnie wybierz pozycję **Rozszerzenia**. Na koniec zaznacz **natywną tablicę SDK matematyczną,** a następnie wybierz przycisk **OK.**

5. Wyświetl właściwości projektu dla NativeMathSDKSample.

    Właściwości zdefiniowane w *pliku NativeMathSDK.props* zostały zastosowane podczas dodawania odwołania. Można sprawdzić, czy właściwości zostały zastosowane, sprawdzając właściwość **katalogów VC++** **właściwości właściwości konfiguracji**projektu .

6. W **Eksploratorze rozwiązań**otwórz stronę **MainPage.xaml**, a następnie użyj następującego kodu XAML, aby zastąpić jego zawartość:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Zaktualizuj *stronę Mainpage.xaml.h,* aby dopasować ten kod:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Zaktualizuj *stronę MainPage.xaml.cpp,* aby dopasować go do tego kodu:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Wybierz klawisz **F5,** aby uruchomić aplikację.

10. W aplikacji wprowadź dowolne dwie liczby, wybierz operację, a następnie wybierz **=** przycisk.

     Pojawi się poprawny wynik.

    W tym przewodniku pokazano, jak utworzyć i używać SDK [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] rozszerzenia do[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] wywołania do biblioteki i biblioteki nie.

## <a name="next-steps"></a>Następne kroki

## <a name="see-also"></a>Zobacz też
- [Instruktaż: Tworzenie sdk przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Tworzenie zestawu do tworzenia oprogramowania](../extensibility/creating-a-software-development-kit.md)
