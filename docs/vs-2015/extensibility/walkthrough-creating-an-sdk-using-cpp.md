---
title: 'Przewodnik: Tworzenie zestawu SDK przy użyciu języka C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202072"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Przewodnik: tworzenie zestawu SDK przy użyciu języka C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak utworzyć natywny zestaw SDK biblioteki matematycznej języka C++, spakować zestaw SDK jako rozszerzenie programu Visual Studio (VSIX), a następnie użyć go do utworzenia aplikacji. Przewodnik jest podzielony na następujące kroki:  
  
- [Aby utworzyć biblioteki natywne i środowisko wykonawcze systemu Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Aby utworzyć projekt rozszerzenia NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Aby utworzyć biblioteki natywne i środowisko wykonawcze systemu Windows  
  
1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.  
  
2. Na liście szablonów rozwiń węzeł **Visual C++**, **Sklep Windows**, a następnie wybierz szablon **Biblioteka DLL (aplikacje do sklepu Windows)** . W polu **Nazwa** Określ `NativeMath` , a następnie wybierz przycisk **OK** .  
  
3. Zaktualizuj NativeMath. h, aby pasował do poniższego kodu.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Zaktualizuj NativeMath. cpp, aby dopasować ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz **Dodaj**, **Nowy projekt**.  
  
6. Na liście szablonów rozwiń węzeł **Visual C++**, a następnie wybierz szablon **środowisko wykonawcze systemu Windows składnika** . W polu **Nazwa** Określ `NativeMathWRT` , a następnie wybierz przycisk **OK** .  
  
7. Zaktualizuj Class1. h, aby dopasować ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Zaktualizuj Class1. cpp, aby dopasować ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. Na pasku menu wybierz **kompilacja**, **Kompiluj rozwiązanie**.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Aby utworzyć projekt rozszerzenia NativeMathVSIX  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz **Dodaj**, **Nowy projekt**.  
  
2. Na liście szablonów rozwiń pozycję **Visual C#**, **rozszerzalność**, a następnie wybierz pozycję **pakiet VSIX**. W polu **Nazwa** Określ **NativeMathVSIX**, a następnie wybierz przycisk **OK** .  
  
3. Gdy pojawi się projektant manifestu VSIX, zamknij go.  
  
4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla elementu **source. Extension. vsixmanifest**, a następnie wybierz polecenie **Wyświetl kod**.  
  
5. Użyj poniższego kodu XML, aby zastąpić istniejący kod XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **NativeMathVSIX** , a następnie wybierz **Dodaj**, **nowy element**.  
  
7. Na liście **elementów języka Visual C#** rozwiń pozycję **dane**, a następnie wybierz pozycję **plik XML**. W polu **Nazwa** Określ `SDKManifest.xml` , a następnie wybierz przycisk **OK** .  
  
8. Użyj tego kodu XML, aby zastąpić zawartość pliku:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. W **Eksplorator rozwiązań**w projekcie **NativeMathVSIX** Utwórz tę strukturę folderów:  
  
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
  
10. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **rozwiązania "NativeMath"**, a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.  
  
11. W **Eksploratorze plików**Skopiuj \NativeMath\NativeMath.h, a następnie w **Eksplorator rozwiązań**, w projekcie **NativeMathVSIX** , wklej go w folderze \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Skopiuj \Debug\NativeMath\NativeMath.lib, a następnie wklej go w folderze \DesignTime\Debug\x86\.  
  
     Skopiuj \Debug\NativeMath\NativeMath.dll i wklej go w folderze \Redist\Debug\x86\.  
  
     Skopiuj DebugNativeMathWRTNativeMathWRT.dll i wklej go w folderze RedistDebugx86.  
  
     Skopiuj plik DebugNativeMathWRTNativeMathWRT. winmd i wklej go w folderze ReferencesCommonConfigurationNeutral.  
  
     Skopiuj plik DebugNativeMathWRTNativeMathWRT. pri i wklej go w folderze ReferencesCommonConfigurationNeutral.  
  
12. W folderze \DesignTime\Debug\x86\ Utwórz plik tekstowy o nazwie NativeMathSDK. props, a następnie wklej w nim następującą zawartość:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Na pasku menu wybierz **Widok**, **inne okna**, **okno właściwości** (klawiatura: wybierz klawisz F4).  
  
14. W obszarze **Eksplorator rozwiązań**wybierz plik **NativeMathWRT. winmd** . W oknie **Właściwości** Zmień właściwość **Akcja kompilacji** na **zawartość**, a następnie zmień wartość właściwości **Dołącz w VSIX** na **true**.  
  
     Powtórz ten proces dla pliku **SimpleMath. pri** .  
  
     Powtórz ten proces dla pliku **NativeMath. lib** .  
  
     Powtórz ten proces dla pliku **NativeMathSDK. props** .  
  
15. W **Eksplorator rozwiązań**wybierz plik **NativeMath. h** . W oknie **Właściwości** Zmień wartość właściwości **Dołącz w VSIX** na **true**.  
  
     Powtórz ten proces dla pliku **NativeMath.dll** .  
  
     Powtórz ten proces dla pliku **NativeMathWRT.dll** .  
  
     Powtórz ten proces dla pliku **SDKManifest.xml** .  
  
16. Na pasku menu wybierz **kompilacja**, **Kompiluj rozwiązanie**.  
  
17. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **NativeMathVSIX** , a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.  
  
18. W **Eksploratorze plików**przejdź do folderu \bin\debug\, a następnie uruchom plik NativeMathVSIX. vsix, aby rozpocząć instalację.  
  
19. Wybierz przycisk **Zainstaluj** , poczekaj na zakończenie instalacji, a następnie ponownie uruchom program Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Aby utworzyć przykładową aplikację, która używa biblioteki klas  
  
1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.  
  
2. Na liście szablonów rozwiń węzeł **Visual C++**, **Sklep Windows**, a następnie wybierz pozycję **pusta aplikacja**. W polu **Nazwa** Określ **NativeMathSDKSample**, a następnie wybierz przycisk **OK** .  
  
3. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **NativeMathSDKSample** , a następnie wybierz **Dodaj**, **odwołanie**.  
  
4. Na stronie właściwości **wspólne**, **Struktura i odwołania** , na liście typów referencyjnych, rozwiń pozycję **Windows**, a następnie wybierz pozycję **rozszerzenia**. W okienku szczegółów wybierz **natywne rozszerzenie zestawu Math SDK** , a następnie wybierz przycisk **Dodaj nowe odwołanie** .  
  
5. W oknie dialogowym **Dodawanie odwołania** zaznacz pole wyboru **natywny zestaw SDK matematycznych** , a następnie wybierz przycisk **OK** .  
  
6. Wyświetl właściwości projektu dla NativeMathSDKSample.  
  
    Właściwości zdefiniowane w NativeMathSDK. props zostały zastosowane po dodaniu odwołania. Można to sprawdzić, sprawdzając Właściwość **katalogów VC + +** **Właściwości konfiguracji**projektu.  
  
7. W **Eksplorator rozwiązań**Otwórz MainPage. XAML, a następnie użyj następującego języka XAML, aby zastąpić jego zawartość:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Zaktualizuj MainPage. XAML. h, aby dopasować ten kod:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Zaktualizuj MainPage. XAML. cpp, aby dopasować ten kod:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Wybierz klawisz F5, aby uruchomić aplikację.  
  
11. W aplikacji wprowadź dwie liczby, wybierz operację, a następnie wybierz **=** przycisk.  
  
     Zostanie wyświetlony prawidłowy wynik.  
  
    W tym instruktażu pokazano, jak utworzyć zestaw SDK rozszerzenia i użyć go do wywołania [!INCLUDE[wrt](../includes/wrt-md.md)] biblioteki i innej niż [!INCLUDE[wrt](../includes/wrt-md.md)] Biblioteka.  
  
## <a name="next-steps"></a>Następne kroki  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie zestawu SDK przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
