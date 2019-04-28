---
title: 'Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++ | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74133386d2dbd6d6b3ccb099a0b9231bc9deb073
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796504"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++
W tym instruktażu pokazano, jak tworzenie natywnych języka C++ matematyczne biblioteki zestawu SDK pakietu SDK jako Visual Studio rozszerzenia (VSIX), a następnie użyć go do tworzenia aplikacji. Instruktażu jest podzielony na następujące kroki:

- [Tworzenie natywnych i bibliotek środowiska uruchomieniowego Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Aby utworzyć projekt rozszerzenia NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="createClassLibrary"></a> Tworzenie natywnych i bibliotek środowiska uruchomieniowego Windows

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

2. Na liście szablonów rozwiń **Visual C++** > **Windows Universal**, a następnie wybierz pozycję **biblioteki DLL (Windows Universal apps)** szablonu. W **nazwa** określ `NativeMath`, a następnie wybierz **OK** przycisku.

3. Aktualizacja *NativeMath.h* aby dopasować następujący kod.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Aktualizacja *NativeMath.cpp* do dopasowania ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz **Dodaj** > **nowy projekt**.

6. Na liście szablonów rozwiń **Visual C++**, a następnie wybierz pozycję **składnika środowiska wykonawczego Windows** szablonu. W **nazwa** określ `NativeMathWRT`, a następnie wybierz **OK** przycisku.

7. Aktualizacja *Class1.h* do dopasowania ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Aktualizacja *Class1.cpp* do dopasowania ten kod:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

## <a name="createVSIX"></a> Aby utworzyć projekt rozszerzenia NativeMathVSIX

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz **Dodaj** > **nowy projekt**.

2. Na liście szablonów rozwiń **Visual C#** > **rozszerzalności**, a następnie wybierz pozycję **projekt VSIX**. W **nazwa** określ **NativeMathVSIX**, a następnie wybierz **OK** przycisku.

3. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **source.extension.vsixmanifest**, a następnie wybierz **Wyświetl kod**.

4. Następujący kod XML można użyć, aby zamienić istniejący plik XML.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **NativeMathVSIX** projektu, a następnie wybierz **Dodaj** > **nowy element**.

6. Na liście **elementy Visual C#**, rozwiń węzeł **danych**, a następnie wybierz pozycję **pliku XML**. W **nazwa** określ `SDKManifest.xml`, a następnie wybierz **OK** przycisku.

7. Zastąp zawartość pliku za pomocą tego XML:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. W **Eksploratora rozwiązań**w obszarze **NativeMathVSIX** projektu, należy utworzyć tej struktury folderów:

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

9. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz **Otwórz Folder w Eksploratorze plików**.

10. W **Eksploratora plików**, kopia *$SolutionRoot$\NativeMath\NativeMath.h*, a następnie w polu **Eksploratora rozwiązań**w obszarze **NativeMathVSIX**projektu, wklej ją w *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  folderu.

     Kopiuj *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*, a następnie wklej go w *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  folderu.

     Kopiuj *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* i wklej go w *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  folderu.

     Kopiuj *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* i wklej go w *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* folderu.
     Kopiuj *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* i wklej go w *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* folderu.

     Kopiuj *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* i wklej go w *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* folderu.

11. W *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  folderze utwórz plik tekstowy o nazwie *NativeMathSDK.props*, a następnie wklej poniższą zawartość w nim:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. Na pasku menu wybierz **widoku** > **Windows inne** > **okno właściwości** (klawiatury: Wybierz **F4** klucza).

13. W **Eksploratora rozwiązań**, wybierz opcję **NativeMathWRT.winmd** pliku. W **właściwości** oknie zmiany **Build Action** właściwości **zawartości**, a następnie zmień **Include w VSIX** właściwości  **Wartość true,**.

     Powtórz ten proces dla **NativeMath.h** pliku.

     Powtórz ten proces dla **NativeMathWRT.pri** pliku.

     Powtórz ten proces dla **NativeMath.Lib** pliku.

     Powtórz ten proces dla **NativeMathSDK.props** pliku.

14. W **Eksploratora rozwiązań**, wybierz opcję **NativeMath.h** pliku. W **właściwości** oknie zmiany **Include w VSIX** właściwości **True**.

     Powtórz ten proces dla **NativeMath.dll** pliku.

     Powtórz ten proces dla **NativeMathWRT.dll** pliku.

     Powtórz ten proces dla **SDKManifest.xml** pliku.

15. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

16. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **NativeMathVSIX** projektu, a następnie wybierz **Otwórz Folder w Eksploratorze plików**.

17. W **Eksploratora plików**, przejdź do *$SolutionRoot$ \NativeMathVSIX\bin\Debug* folder, a następnie uruchom *NativeMathVSIX.vsix* do rozpoczęcia instalacji.

18. Wybierz **zainstalować** przycisk, poczekaj na zakończenie instalacji, a następnie otwórz program Visual Studio.

## <a name="createSample"></a> Aby utworzyć przykładową aplikację, która używa biblioteki klas

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

2. Na liście szablonów rozwiń **Visual C++** > **Windows Universal** , a następnie wybierz **pusta aplikacja**. W **nazwa** określ **NativeMathSDKSample**, a następnie wybierz **OK** przycisku.

3. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **NativeMathSDKSample** projektu, a następnie wybierz **Dodaj** > **odwołania**.

4. W **Dodaj odwołanie** Rozwiń okno dialogowe, na liście typów referencyjnych **Universal Windows**, a następnie wybierz pozycję **rozszerzenia**. Na koniec wybierz pozycję **natywnym zestawem SDK matematyczne** pole wyboru, a następnie wybierz **OK** przycisku.

5. Wyświetl właściwości projektu dla NativeMathSDKSample.

    Właściwości, które zostały zdefiniowane w *NativeMathSDK.props* zostały zastosowane podczas dodawania odwołania. Możesz sprawdzić właściwości zostały zastosowane, sprawdzając **katalogi VC ++** właściwości projektu **właściwości konfiguracji**.

6. W **Eksploratora rozwiązań**, otwórz **MainPage.xaml**, a następnie zastąp jego zawartość za pomocą następujących XAML:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Aktualizacja *pliku Mainpage.xaml.h* do dopasowania ten kod:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Aktualizacja *MainPage.xaml.cpp* do dopasowania ten kod:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Wybierz **F5** klawisz, aby uruchomić aplikację.

10. W aplikacji, wprowadź dowolne dwie liczby, umożliwia wybranie operacji, a następnie wybierz **=** przycisku.

     Zostanie wyświetlony odpowiedni wynik.

    W tym przewodniku pokazano, jak utworzyć i wywoływać przy użyciu zestawu SDK rozszerzenia [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteki i innej niż[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteki.

## <a name="next-steps"></a>Następne kroki

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Tworzenie za pomocą zestawu SDK C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Utwórz zestaw software development kit](../extensibility/creating-a-software-development-kit.md)
