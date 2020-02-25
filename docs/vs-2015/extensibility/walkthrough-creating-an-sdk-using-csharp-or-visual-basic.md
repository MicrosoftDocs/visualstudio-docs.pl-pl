---
title: 'Przewodnik: Tworzenie zestawu SDK przy C# użyciu lub Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558209"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Przewodnik: tworzenie zestawu SDK przy użyciu języka C# lub Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu dowiesz się, jak utworzyć prosty zestaw SDK biblioteki matematycznej za pomocą C# wizualizacji, a następnie spakować zestaw SDK jako rozszerzenie programu Visual Studio (VSIX). Należy wykonać następujące procedury:  
  
- [Aby utworzyć składnik środowisko wykonawcze systemu Windows SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [Aby utworzyć projekt rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="createClassLibrary"></a>Aby utworzyć składnik środowisko wykonawcze systemu Windows SimpleMath  
  
1. Na pasku menu wybierz **plik**, **Nowy**, **Nowy projekt**.  
  
2. Na liście szablonów rozwiń węzeł  **C# Visual** lub **Visual Basic**, wybierz węzeł **Sklep Windows** , a następnie wybierz szablon **składnika Środowisko wykonawcze systemu Windows** .  
  
3. W polu **Nazwa** Określ **SimpleMath**, a następnie wybierz przycisk **OK** .  
  
4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu **SimpleMath** , a następnie wybierz polecenie **Właściwości**.  
  
5. Zmień nazwę **Class1.cs** na **arithmetic.cs** i zaktualizuj ją tak, aby pasowała do następującego kodu:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **rozwiązanie "SimpleMath"** , a następnie wybierz pozycję **Configuration Manager**.  
  
     Zostanie otwarte okno dialogowe **Configuration Manager** .  
  
7. Na liście **Konfiguracja rozwiązania aktywnego** wybierz pozycję **Zwolnij**.  
  
8. W kolumnie **Konfiguracja** Sprawdź, czy wiersz **SimpleMath** jest ustawiony na wartość **Zwolnij**, a następnie wybierz przycisk **Zamknij** , aby zaakceptować zmianę.  
  
    > [!IMPORTANT]
    > Zestaw SDK dla składnika SimpleMath zawiera tylko jedną konfigurację. Ta konfiguracja musi być kompilacją wydania lub aplikacje korzystające ze składnika nie przekazują certyfikacji dla[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].  
  
9. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu **SimpleMath** , a następnie wybierz polecenie **Kompiluj**.  
  
## <a name="createVSIX"></a>Aby utworzyć projekt rozszerzenia SimpleMathVSIX  
  
1. W menu skrótów węzła **"SimpleMath" rozwiązania** wybierz pozycję **Dodaj**, **Nowy projekt**.  
  
2. Na liście szablonów rozwiń pozycję  **C# Wizualizacja** lub **Visual Basic**, wybierz węzeł **rozszerzalności** , a następnie wybierz szablon **projektu VSIX** .  
  
3. W polu **Nazwa** Określ **SimpleMathVSIX**, a następnie wybierz przycisk **OK** .  
  
4. W **Eksplorator rozwiązań**wybierz element **source. Extension. vsixmanifest** .  
  
5. Na pasku menu wybierz **Widok**, **kod**.  
  
6. Zastąp istniejący kod XML następującym kodem XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. W **Eksplorator rozwiązań**wybierz projekt **SimpleMathVSIX** .  
  
8. Na pasku menu wybierz **projekt**, **Dodaj nowy element**.  
  
9. Na liście **elementów wspólnych**rozwiń pozycję **dane**, a następnie wybierz pozycję **plik XML**.  
  
10. W polu **Nazwa** Określ `SDKManifest.xml`, a następnie wybierz przycisk **Dodaj** .  
  
11. W **Eksplorator rozwiązań**Otwórz menu skrótów dla `SDKManifest.xml`, wybierz **Właściwości**, a następnie zmień wartość właściwości **include in VSIX** na **true**.  
  
12. Zastąp zawartość pliku następującym kodem XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **SimpleMathVSIX** , wybierz **Dodaj**, a następnie wybierz **Nowy folder**.  
  
14. Zmień nazwę folderu na `references`.  
  
15. Otwórz menu skrótów dla folderu **References** , wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy folder**.  
  
16. Zmień nazwę podfolderu na `commonconfiguration`, utwórz podfolder w nim i nazwij podfolder `neutral`.  
  
17. Powtórz poprzednie cztery kroki, tym razem zmieniając nazwę pierwszego folderu na `redist`.  
  
     Projekt zawiera teraz następującą strukturę folderów:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **SimpleMath** , a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.  
  
19. W **Eksploratorze plików**przejdź do folderu bin\Release, otwórz menu skrótów dla pliku SimpleMath. winmd, a następnie wybierz polecenie **Kopiuj**.  
  
20. W **Eksplorator rozwiązań**wklej plik do folderu references\commonconfiguration\neutral w projekcie **SimpleMathVSIX** .  
  
21. Powtórz poprzedni krok, wklejając plik SimpleMath. pri do folderu redist\commonconfiguration\neutral w projekcie **SimpleMathVSIX** .  
  
22. W **Eksplorator rozwiązań**wybierz **SimpleMath. winmd**.  
  
23. Na pasku menu wybierz **Widok**, **Właściwości** (klawiatura: wybierz klawisz F4).  
  
24. W oknie **Właściwości** Zmień właściwość **Akcja kompilacji** na **zawartość**, a następnie zmień wartość właściwości **Dołącz w VSIX** na **true**.  
  
25. W **Eksplorator rozwiązań**Powtórz ten proces dla **SimpleMath. pri**.  
  
26. W **Eksplorator rozwiązań**wybierz projekt **SimpleMathVSIX** .  
  
27. Na pasku menu wybierz **kompilacja**, **kompilacja SimpleMathVSIX**.  
  
28. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **SimpleMathVSIX** , a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików**.  
  
29. W **Eksploratorze plików**przejdź do folderu \bin\Release, a następnie uruchom plik SimpleMathVSIX. vsix, aby go zainstalować.  
  
30. Wybierz przycisk **Zainstaluj** , poczekaj na zakończenie instalacji, a następnie ponownie uruchom program Visual Studio.  
  
## <a name="createSample"></a>Aby utworzyć przykładową aplikację, która używa biblioteki klas  
  
1. Na pasku menu wybierz **plik**, **Nowy**, **Nowy projekt**.  
  
2. Na liście szablonów rozwiń węzeł **Visual C#**  lub **Visual Basic**, a następnie wybierz węzeł **Sklep Windows** .  
  
3. Wybierz szablon **pustej aplikacji** , nazwij projekt **ArithmeticUI**, a następnie wybierz przycisk **OK** .  
  
4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ArithmeticUI** , a następnie wybierz **Dodaj**, **odwołanie**.  
  
5. Na liście typów odwołań rozwiń węzeł **Windows**, a następnie wybierz pozycję **rozszerzenia**.  
  
6. W okienku szczegółów wybierz **proste rozszerzenie Math SDK** .  
  
    Pojawią się dodatkowe informacje o zestawie SDK. Możesz wybrać link **więcej informacji** , aby otworzyć https://docs.microsoft.com, jak określono w pliku SDKManifest. XML wcześniej w tym instruktażu.  
  
7. W oknie dialogowym **Menedżer odwołań** zaznacz pole wyboru **prosty zestaw SDK** , a następnie wybierz przycisk **OK** .  
  
8. Na pasku menu wybierz **Widok**, **Przeglądarka obiektów**.  
  
9. Na liście **Przeglądaj** wybierz pozycję **proste matematyczne**.  
  
     Teraz możesz dowiedzieć się, co znajduje się w zestawie SDK.  
  
10. W **Eksplorator rozwiązań**Otwórz MainPage. XAML i Zastąp jego zawartość następującym XAML:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Zaktualizuj MainPage.xaml.cs tak, aby pasował do następującego kodu:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Wybierz klawisz F5, aby uruchomić aplikację.  
  
13. W aplikacji wprowadź dwie liczby, wybierz operację, a następnie wybierz przycisk **=** .  
  
     Zostanie wyświetlony prawidłowy wynik.  
  
    Pomyślnie utworzono i zastosowano zestaw SDK rozszerzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie zestawu SDK przy C++ użyciu](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Przewodnik: Tworzenie zestawu SDK przy użyciu  JavaScript](walkthrough-creating-an-sdk-using-javascript.md)  
 [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
