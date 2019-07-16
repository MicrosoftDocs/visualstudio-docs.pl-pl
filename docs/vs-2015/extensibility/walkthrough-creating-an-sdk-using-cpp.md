---
title: 'Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++ | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202072"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak tworzenie natywnych języka C++ matematyczne biblioteki zestawu SDK pakietu SDK jako Visual Studio rozszerzenia (VSIX), a następnie użyć go do tworzenia aplikacji. Instruktażu jest podzielony na następujące kroki:  
  
- [Tworzenie natywnych i bibliotek środowiska uruchomieniowego Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Aby utworzyć projekt rozszerzenia NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="createClassLibrary"></a> Tworzenie natywnych i bibliotek środowiska uruchomieniowego Windows  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. Na liście szablonów rozwiń **Visual C++** , **Windows Store**, a następnie wybierz pozycję **biblioteki DLL (aplikacje Windows Store)** szablonu. W **nazwa** określ `NativeMath`, a następnie wybierz **OK** przycisku.  
  
3. Zaktualizuj NativeMath.h, aby dopasować następujący kod.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. NativeMath.cpp aktualizacja odpowiadający ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **rozwiązania "NativeMath"** , a następnie wybierz **Dodaj**, **nowy projekt**.  
  
6. Na liście szablonów rozwiń **Visual C++** , a następnie wybierz pozycję **składnika środowiska wykonawczego Windows** szablonu. W **nazwa** określ `NativeMathWRT`, a następnie wybierz **OK** przycisku.  
  
7. Class1.h aktualizacja odpowiadający ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Class1.cpp aktualizacja odpowiadający ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
## <a name="createVSIX"></a> Aby utworzyć projekt rozszerzenia NativeMathVSIX  
  
1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **rozwiązania "NativeMath"** , a następnie wybierz **Dodaj**, **nowy projekt**.  
  
2. Na liście szablonów rozwiń **Visual C#** , **rozszerzalności**, a następnie wybierz pozycję **pakiet VSIX**. W **nazwa** określ **NativeMathVSIX**, a następnie wybierz **OK** przycisku.  
  
3. Kiedy wyświetli się Projektant manifestu VSIX, zamknij go.  
  
4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **source.extension.vsixmanifest**, a następnie wybierz **Wyświetl kod**.  
  
5. Następujący kod XML można użyć, aby zamienić istniejący plik XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **NativeMathVSIX** projektu, a następnie wybierz **Dodaj**, **nowy element**.  
  
7. Na liście **elementy Visual C#** , rozwiń węzeł **danych**, a następnie wybierz pozycję **pliku XML**. W **nazwa** określ `SDKManifest.xml`, a następnie wybierz **OK** przycisku.  
  
8. Zastąp zawartość pliku za pomocą tego XML:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. W **Eksploratora rozwiązań**w **NativeMathVSIX** projektu, należy utworzyć tej struktury folderów:  
  
    ```  
  
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
  
10. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **rozwiązania "NativeMath"** , a następnie wybierz **Otwórz Folder w Eksploratorze plików**.  
  
11. W **Eksploratora plików**, skopiuj \NativeMath\NativeMath.h, a następnie w polu **Eksploratora rozwiązań**w **NativeMathVSIX** projektu, wklej go w \DesignTime\ CommonConfiguration\Neutral\Include\ folder.  
  
     Skopiuj \Debug\NativeMath\NativeMath.lib, a następnie wklej go w folderze \DesignTime\Debug\x86\.  
  
     \Debug\NativeMath\NativeMath.dll skopiuj i wklej go w folderze \Redist\Debug\x86\.  
  
     DebugNativeMathWRTNativeMathWRT.dll skopiuj i wklej go w folderze RedistDebugx86.  
  
     DebugNativeMathWRTNativeMathWRT.winmd skopiuj i wklej go w folderze ReferencesCommonConfigurationNeutral.  
  
     DebugNativeMathWRTNativeMathWRT.pri skopiuj i wklej go w folderze ReferencesCommonConfigurationNeutral.  
  
12. W folderze \DesignTime\Debug\x86\ Utwórz plik tekstowy, który nosi nazwę NativeMathSDK.props, a następnie wklej poniższą zawartość w nim:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Na pasku menu wybierz **widoku**, **Windows inne**, **okno właściwości** (klawiatury: Wybierz klawisz F4).  
  
14. W **Eksploratora rozwiązań**, wybierz opcję **NativeMathWRT.winmd** pliku. W **właściwości** oknie zmiany **Build Action** właściwości **zawartości**, a następnie zmień **Include w VSIX** właściwości  **Wartość true,** .  
  
     Powtórz ten proces dla **SimpleMath.pri** pliku.  
  
     Powtórz ten proces dla **NativeMath.Lib** pliku.  
  
     Powtórz ten proces dla **NativeMathSDK.props** pliku.  
  
15. W **Eksploratora rozwiązań**, wybierz opcję **NativeMath.h** pliku. W **właściwości** oknie zmiany **Include w VSIX** właściwości **True**.  
  
     Powtórz ten proces dla **NativeMath.dll** pliku.  
  
     Powtórz ten proces dla **NativeMathWRT.dll** pliku.  
  
     Powtórz ten proces dla **SDKManifest.xml** pliku.  
  
16. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
17. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **NativeMathVSIX** projektu, a następnie wybierz **Otwórz Folder w Eksploratorze plików**.  
  
18. W **Eksploratora plików**, przejdź do folderu \bin\Debug\, a następnie uruchom NativeMathVSIX.vsix, aby rozpocząć instalację.  
  
19. Wybierz **zainstalować** przycisk, poczekaj na zakończenie instalacji i ponownie uruchom program Visual Studio.  
  
## <a name="createSample"></a> Aby utworzyć przykładową aplikację, która używa biblioteki klas  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. Na liście szablonów rozwiń **Visual C++** , **Windows Store**, a następnie wybierz pozycję **pusta aplikacja**. W **nazwa** określ **NativeMathSDKSample**, a następnie wybierz **OK** przycisku.  
  
3. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **NativeMathSDKSample** projektu, a następnie wybierz **Dodaj**, **odwołania**.  
  
4. Na **wspólne właściwości**, **szablon i odwołania** rozwiń strony właściwości, na liście typów referencyjnych **Windows**, a następnie wybierz pozycję **rozszerzenia** . W okienku szczegółów wybierz **natywnym zestawem SDK matematyczne** rozszerzenie, a następnie wybierz **Dodaj nowe odwołanie** przycisku.  
  
5. W **Dodaj odwołanie** okno dialogowe, wybierz opcję **natywnym zestawem SDK matematyczne** pole wyboru, a następnie wybierz **OK** przycisku.  
  
6. Wyświetl właściwości projektu dla NativeMathSDKSample.  
  
    Właściwości, które zostały zdefiniowane w NativeMathSDK.props zostały zastosowane podczas dodawania odwołania. Można to sprawdzić, analizując **katalogi VC ++** właściwości projektu **właściwości konfiguracji**.  
  
7. W **Eksploratora rozwiązań**, otwórz plik MainPage.xaml i następnie zastąp jego zawartość za pomocą następujących XAML:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Aktualizowanie pliku Mainpage.xaml.h, aby dopasować ten kod:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. MainPage.xaml.cpp aktualizacja odpowiadający ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Wybierz klawisz F5, aby uruchomić aplikację.  
  
11. W aplikacji, wprowadź dowolne dwie liczby, umożliwia wybranie operacji, a następnie wybierz **=** przycisku.  
  
     Zostanie wyświetlony odpowiedni wynik.  
  
    W tym przewodniku pokazano, jak utworzyć i wywoływać przy użyciu zestawu SDK rozszerzenia [!INCLUDE[wrt](../includes/wrt-md.md)] biblioteki i innej niż[!INCLUDE[wrt](../includes/wrt-md.md)] biblioteki.  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie za pomocą zestawu SDK C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
