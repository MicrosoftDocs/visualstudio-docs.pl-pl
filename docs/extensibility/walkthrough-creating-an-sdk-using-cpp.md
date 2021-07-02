---
title: 'Przewodnik: tworzenie zestawu SDK przy użyciu języka C++ | Microsoft Docs'
description: Dowiedz się, jak utworzyć natywny zestaw SDK biblioteki matematycznej języka C++, spakować zestaw SDK jako rozszerzenie Visual Studio, a następnie użyć go do utworzenia aplikacji przy użyciu tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a52322e575dc201a6bf1648af93d813828e0b17
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113223010"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Przewodnik: tworzenie zestawu SDK przy użyciu języka C++
W tym przewodniku pokazano, jak utworzyć natywny zestaw SDK biblioteki matematycznej języka C++, spakować zestaw SDK jako rozszerzenie Visual Studio (VSIX), a następnie użyć go do utworzenia aplikacji. Przewodnik jest podzielony na następujące kroki:

- [Aby utworzyć natywne i Windows uruchomieniowe](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Aby utworzyć projekt rozszerzenia NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Aby utworzyć przykładową aplikację, która używa biblioteki klas](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Wymagania wstępne
 Aby postępować zgodnie z tym instruktażem, musisz zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Aby utworzyć natywne i Windows uruchomieniowe

1. Na pasku menu wybierz pozycję **Nowy** plik  >    >  **Project**.

2. Na liście szablonów rozwiń pozycję Visual C++ Windows , a następnie wybierz szablon DLL  >   **(Windows aplikacje uniwersalne).** W polu **Nazwa** określ wartość `NativeMath` , a następnie wybierz przycisk **OK.**

3. Zaktualizuj *kod NativeMath.h,* aby był zgodne z poniższym kodem.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. Zaktualizuj *kod NativeMath.cpp,* aby był zgodne z tym kodem:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. W Eksplorator rozwiązań otwórz menu skrótów dla pozycji **Rozwiązanie "NativeMath",** a następnie wybierz pozycję **Dodaj** nowy   >  **Project**.

6. Na liście szablonów rozwiń pozycję **Visual C++**, a następnie wybierz **szablon Windows uruchomieniowego.** W polu **Nazwa** określ wartość `NativeMathWRT` , a następnie wybierz przycisk **OK.**

7. Zaktualizuj *klasę Class1.h,* aby była dopasowana do tego kodu:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. Zaktualizuj *klasę Class1.cpp,* aby była dopasowana do tego kodu:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. Na pasku menu wybierz pozycję Build Build Solution **(Skompilowanie**  >  **rozwiązania kompilacji).**

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Aby utworzyć projekt rozszerzenia NativeMathVSIX

1. W Eksplorator rozwiązań otwórz menu skrótów dla pozycji **Rozwiązanie "NativeMath",** a następnie wybierz pozycję **Dodaj** nowy   >  **Project**.

2. Na liście szablonów rozwiń pozycję **Rozszerzalność Visual C#,**  >  a następnie wybierz pozycję **VSIX Project**. W polu **Nazwa** określ wartość **NativeMathVSIX,** a następnie wybierz **przycisk OK.**

3. W **Eksplorator rozwiązań** otwórz menu skrótów **source.extension.vsixmanifest,** a następnie wybierz **pozycję Wyświetl kod**.

4. Użyj następującego kodu XML, aby zastąpić istniejący kod XML.

    ```xml
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="NativeMathVSIX..c6b3cae1-e7e2-4e71-90f6-21017ea0dff7" Version="1.0" Language="en-US" Publisher="MyName" />
        <DisplayName>Native Math SDK</DisplayName>
        <Description>Native Math Library w/ Windows Runtime Additions</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="NativeMathSDK" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

5. W **Eksplorator rozwiązań** otwórz menu skrótów dla projektu **NativeMathVSIX,** a następnie wybierz **pozycję Dodaj** nowy  >  **element**.

6. Na liście elementów **Visual C# rozwiń** pozycję **Dane,** a następnie wybierz pozycję **Plik XML.** W polu **Nazwa** określ wartość `SDKManifest.xml` , a następnie wybierz przycisk **OK.**

7. Użyj tego kodu XML, aby zastąpić zawartość pliku:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. W **Eksplorator rozwiązań** w **projekcie NativeMathVSIX** utwórz tę strukturę folderów:

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

9. W Eksplorator rozwiązań otwórz menu skrótów dla pozycji **Rozwiązanie "NativeMath",** a następnie wybierz pozycję **Otwórz folder** w Eksplorator plików . 

10. W programie **Eksplorator plików** skopiuj wartość *$SolutionRoot$\NativeMath\NativeMath.h,* a następnie w pliku **Eksplorator rozwiązań** w projekcie **NativeMathVSIX** wklej go w folderze *$SolutionRoot$\NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include. \\*

     Skopiuj *$SolutionRoot$\Debug\NativeMath\NativeMath.lib,* a następnie wklej go w *folderze $SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86. \\*

     Skopiuj *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* i wklej go w *folderze $SolutionRoot$\NativeMathVSIX\Redist\Debug\x86. \\*

     Skopiuj *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* i wklej go w *folderze $SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*
     Skopiuj *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* i wklej go w *folderze $SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

     Skopiuj *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* i wklej go w *folderze $SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

11. W *folderze $SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86 \\* utwórz plik tekstowy o nazwie *NativeMathSDK.props,* a następnie wklej do niego następującą zawartość:
   
    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <NativeMathSDKPath>$(FrameworkSDKRoot)\..\..\UAP\v0.8.0.0\ExtensionSDKs\NativeMathSDK\1.0\</NativeMathSDKPath>
        <IncludePath>$(NativeMathSDKPath)DesignTime\CommonConfiguration\Neutral\Include;$(IncludePath)</IncludePath>
        <LibraryPath>$(NativeMathSDKPath)DesignTime\Debug\x86;$(LibraryPath)</LibraryPath>
      </PropertyGroup>
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
         <Link>
           <AdditionalDependencies>NativeMath.lib;%(AdditionalDependencies)</AdditionalDependencies>
         </Link>
      </ItemDefinitionGroup>
    </Project>
    ```

12. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne Windows**  >  **właściwości** (Klawiatura: wybierz **klawisz F4).**

13. W **Eksplorator rozwiązań** wybierz plik **NativeMathWRT.winmd.** W **oknie Właściwości** zmień właściwość **Akcja kompilacji** na **Wartość**, a następnie zmień właściwość Uwzględnij w **VSIX** na **True.**

     Powtórz ten proces dla **pliku NativeMath.h.**

     Powtórz ten proces dla pliku **NativeMathWRT.pri.**

     Powtórz ten proces dla **pliku NativeMath.Lib.**

     Powtórz ten proces dla pliku **NativeMathSDK.props.**

14. W **Eksplorator rozwiązań** wybierz plik **NativeMath.h.** W **oknie Właściwości** zmień właściwość **Include in VSIX** na **True.**

     Powtórz ten proces dla **NativeMath.dll** plików.

     Powtórz ten proces dla **NativeMathWRT.dll** plików.

     Powtórz ten proces dla **SDKManifest.xml** plików.

15. Na pasku menu wybierz pozycję Build Build Solution **(Skompilowanie**  >  **rozwiązania kompilacji).**

16. W **Eksplorator rozwiązań** otwórz menu skrótów dla projektu **NativeMathVSIX,** a następnie wybierz pozycję **Otwórz folder** w Eksplorator plików .

17. W **Eksplorator plików** przejdź do folderu *$SolutionRoot$\NativeMathVSIX\bin\Debug,* a następnie uruchom plik *NativeMathVSIX.vsix,* aby rozpocząć instalację.

18. Wybierz przycisk **Zainstaluj,** poczekaj na zakończenie instalacji, a następnie otwórz Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Aby utworzyć przykładową aplikację, która używa biblioteki klas

1. Na pasku menu wybierz pozycję **Nowy** plik  >    >  **Project**.

2. Na liście szablonów rozwiń pozycję Visual C++   >  **Windows uniwersalną, a** następnie wybierz pozycję **Pusta aplikacja.** W polu **Nazwa** określ wartość **NativeMathSDKSample,** a następnie wybierz przycisk **OK.**

3. W **Eksplorator rozwiązań** otwórz menu skrótów dla projektu **NativeMathSDKSample,** a następnie wybierz pozycję **Dodaj**  >  **odwołanie.**

4. W **oknie dialogowym** Dodawanie odwołania na liście typów odwoływczych rozwiń pozycję Universal **Windows**, a następnie wybierz **pozycję Rozszerzenia**. Na koniec zaznacz pole wyboru **Native Math SDK (Natywny zestaw SDK obliczeń matematycznych),** a następnie wybierz **przycisk OK.**

5. Wyświetl właściwości projektu nativeMathSDKSample.

    Właściwości zdefiniowane w pliku *NativeMathSDK.props* zostały zastosowane podczas dodano odwołanie. Możesz sprawdzić, czy właściwości zostały zastosowane, sprawdzając właściwość **Katalogi VC++** właściwości **konfiguracji projektu**.

6. W **Eksplorator rozwiązań** pliku otwórz **mainpage.xaml,** a następnie użyj następującego kodu XAML, aby zastąpić jego zawartość:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. Zaktualizuj *element Mainpage.xaml.h,* aby był zgodne z tym kodem:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. Zaktualizuj *element MainPage.xaml.cpp,* aby był zgodne z tym kodem:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. Wybierz klawisz **F5,** aby uruchomić aplikację.

10. W aplikacji wprowadź dowolne dwie liczby, wybierz operację, a następnie wybierz **=** przycisk.

     Zostanie wyświetlony prawidłowy wynik.

    W tym przewodniku popisano sposób tworzenia i używania zestawu SDK rozszerzeń do wywołania biblioteki [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] i biblioteki [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] spoza biblioteki.

## <a name="next-steps"></a>Następne kroki

## <a name="see-also"></a>Zobacz też
- [Przewodnik: tworzenie zestawu SDK przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Tworzenie zestawu dewelopera oprogramowania](../extensibility/creating-a-software-development-kit.md)
