---
title: 'Przewodnik: Tworzenie za pomocą zestawu SDK C# lub Visual Basic | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 44b1083a9de4a5fe3e86ae37814f6df85f8c1e56
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435494"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Przewodnik: Tworzenie zestawu SDK przy użyciu języka C# lub Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku dowiesz się, jak utworzyć prosty zestaw SDK biblioteki matematyczne przy użyciu języka Visual C# i następnie pakietu SDK jako programu Visual Studio rozszerzenia (VSIX). Wykonasz następujące procedury:  
  
- [Aby utworzyć składnika środowiska wykonawczego Windows SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [Aby utworzyć projekt rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="createClassLibrary"></a> Aby utworzyć składnika środowiska wykonawczego Windows SimpleMath  
  
1. Na pasku menu wybierz **pliku**, **New**, **nowy projekt**.  
  
2. Na liście szablonów rozwiń **Visual C#** lub **języka Visual Basic**, wybierz **Windows Store** węzła, a następnie wybierz **składnika środowiska wykonawczego Windows** szablonu.  
  
3. W **nazwa** określ **SimpleMath**, a następnie wybierz **OK** przycisku.  
  
4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMath** węzła projektu, a następnie wybierz **właściwości**.  
  
5. Zmień nazwę **Class1.cs** do **Arithmetic.cs** i zaktualizować je, aby dopasować następujący kod:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **rozwiązania "SimpleMath"** węzła, a następnie wybierz **programu Configuration Manager**.  
  
     **Programu Configuration Manager** zostanie otwarte okno dialogowe.  
  
7. W **Konfiguracja rozwiązania aktywnego** wybierz **wersji**.  
  
8. W **konfiguracji** kolumny, upewnij się, że **SimpleMath** wiersza jest ustawiona na **wersji**, a następnie wybierz **Zamknij** przycisk, aby zaakceptować Zmiana.  
  
    > [!IMPORTANT]
    > Zestaw SDK dla składnika SimpleMath zawiera tylko jedną konfigurację. Ta konfiguracja musi być kompilacji wydania lub aplikacje, które używają składnika nie przekaże certyfikacji[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMath** węzła projektu, a następnie wybierz **kompilacji**.  
  
## <a name="createVSIX"></a> Aby utworzyć projekt rozszerzenia SimpleMathVSIX  
  
1. W menu skrótów dla **rozwiązania "SimpleMath"** węzła, wybierz **Dodaj**, **nowy projekt**.  
  
2. Na liście szablonów rozwiń **Visual C#** lub **języka Visual Basic**, wybierz **rozszerzalności** węzła, a następnie wybierz **projekt VSIX** szablon.  
  
3. W **nazwa** określ **SimpleMathVSIX**, a następnie wybierz **OK** przycisku.  
  
4. W **Eksploratora rozwiązań**, wybierz **source.extension.vsixmanifest** elementu.  
  
5. Na pasku menu wybierz **widoku**, **kodu**.  
  
6. Zastąp istniejący kod XML następujący kod XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. W **Eksploratora rozwiązań**, wybierz **SimpleMathVSIX** projektu.  
  
8. Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
9. Na liście **wspólne elementy**, rozwiń węzeł **danych**, a następnie wybierz **pliku XML**.  
  
10. W **nazwa** określ `SDKManifest.xml`, a następnie wybierz **Dodaj** przycisku.  
  
11. W **Eksploratora rozwiązań**, otwórz menu skrótów dla `SDKManifest.xml`, wybierz **właściwości**, a następnie zmień wartość **Include w VSIX** właściwość **True**.  
  
12. Zastąp zawartość pliku następujący kod XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMathVSIX** projektu, wybierz **Dodaj**, a następnie wybierz **nowy Folder**.  
  
14. Zmień nazwę folderu do `references`.  
  
15. Otwórz menu skrótów dla **odwołania** folderu, wybierz **Dodaj**, a następnie wybierz **nowy Folder**.  
  
16. Zmień nazwę podfolderu, aby `commonconfiguration`, utwórz podfolder w niej i nazwa podfolderu `neutral`.  
  
17. Powtórz poprzednie cztery kroki tej chwili, zmiana nazwy pierwszego folderu do `redist`.  
  
     Projekt obecnie zawiera następującą strukturę folderów:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMath** projektu, a następnie wybierz **Otwórz Folder w Eksploratorze plików**.  
  
19. W **Eksploratora plików**, przejdź do folderu bin\Release, otwórz menu skrótów dla pliku SimpleMath.winmd, a następnie wybierz **kopiowania**.  
  
20. W **Eksploratora rozwiązań**, wklej go do folderu references\commonconfiguration\neutral w **SimpleMathVSIX** projektu.  
  
21. Powtórz poprzedni krok, wklejanie SimpleMath.pri plik do folderu redist\commonconfiguration\neutral **SimpleMathVSIX** projektu.  
  
22. W **Eksploratora rozwiązań**, wybierz **SimpleMath.winmd**.  
  
23. Na pasku menu wybierz **widoku**, **właściwości** (klawiatury: Wybierz klawisz F4).  
  
24. W **właściwości** oknie zmiany **Build Action** właściwości **zawartości**, a następnie zmień **Include w VSIX** właściwości  **Wartość true,**.  
  
25. W **Eksploratora rozwiązań**, powtórz ten proces dla **SimpleMath.pri**.  
  
26. W **Eksploratora rozwiązań**, wybierz **SimpleMathVSIX** projektu.  
  
27. Na pasku menu wybierz **kompilacji**, **kompilacji SimpleMathVSIX**.  
  
28. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SimpleMathVSIX** projektu, a następnie wybierz **Otwórz Folder w Eksploratorze plików**.  
  
29. W **Eksploratora plików**, przejdź do folderu \bin\Release, a następnie uruchom SimpleMathVSIX.vsix go zainstalować.  
  
30. Wybierz **zainstalować** przycisk, poczekaj na zakończenie instalacji i ponownie uruchom program Visual Studio.  
  
## <a name="createSample"></a> Aby utworzyć przykładową aplikację, która używa biblioteki klas  
  
1. Na pasku menu wybierz **pliku**, **New**, **nowy projekt**.  
  
2. Na liście szablonów rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz **Windows Store** węzła.  
  
3. Wybierz **pusta aplikacja** szablonu, nazwę projektu **ArithmeticUI**, a następnie wybierz **OK** przycisku.  
  
4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ArithmeticUI** projektu, a następnie wybierz **Dodaj**, **odwołania**.  
  
5. Na liście typów referencyjnych rozwiń **Windows**, a następnie wybierz **rozszerzenia**.  
  
6. W okienku szczegółów wybierz **proste SDK matematyczne** rozszerzenia.  
  
    Pojawi się dodatkowe informacje na temat zestawu SDK. Możesz wybrać **więcej informacji o** link umożliwiający otworzenie http://www.msdn.microsoft.com, jak określono w pliku SDKManifest.xml we wcześniejszej części tego przewodnika.  
  
7. W **Menadżer odwołań** okno dialogowe, wybierz opcję **proste SDK matematyczne** pole wyboru, a następnie wybierz **OK** przycisku.  
  
8. Na pasku menu wybierz **widoku**, **przeglądarki obiektów**.  
  
9. W **Przeglądaj** wybierz **proste matematyczne**.  
  
     Można teraz zbadać, co nowego w zestawie SDK.  
  
10. W **Eksploratora rozwiązań**, otwórz plik MainPage.xaml i zastąp jego zawartość następujących XAML:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Zaktualizuj MainPage.xaml.cs, aby dopasować następujący kod:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Wybierz klawisz F5, aby uruchomić aplikację.  
  
13. W aplikacji, wprowadź dowolne dwie liczby, wybierz operację, a następnie wybierz **=** przycisku.  
  
     Zostanie wyświetlony odpowiedni wynik.  
  
    Pomyślnie tworzone i używane rozszerzenie SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Przewodnik: Tworzenie zestawu SDK przy użyciu języka JavaScript](walkthrough-creating-an-sdk-using-javascript.md)   
 [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
