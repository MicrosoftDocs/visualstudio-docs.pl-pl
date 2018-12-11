---
title: Migrowanie usługi języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 412b09016a3f889e0d6c5e40ff75895d5ae8ff48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135860"
---
# <a name="migrating-a-legacy-language-service"></a>Migrowanie usługi języka starsza wersja
Aktualizowanie projektu i dodawanie pliku source.extension.vsixmanifest do projektu, można migrować usługi starszej wersji języka do nowszej wersji programu Visual Studio. Sama usługa języka będzie działał jak wcześniej, ponieważ w edytorze programu Visual Studio dostosowuje go.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej o nowy sposób wdrożenia usługi języka, zobacz [edytora i rozszerzenia usługi języka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrowanie do nowszej wersji programu Visual Studio 2008 języka usługi rozwiązania  
 Poniższe kroki przedstawiają sposób dostosowania o nazwie RegExLanguageService próbki programu Visual Studio 2008. W tym przykładzie w instalacji programu Visual Studio 2008 SDK, można znaleźć w *ścieżki instalacji programu Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ folderu.  
  
> [!IMPORTANT]
>  Jeśli usługi języka nie definiuje kolory, musisz jawnie ustawić <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> do `true` na pakiet VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Aby przeprowadzić migrację usługi języka Visual Studio 2008 do nowszej wersji.  
  
1.  Zainstaluj nowszych wersji programu Visual Studio i programu Visual Studio SDK. Aby uzyskać więcej informacji na temat metody instalowania zestawu SDK, zobacz [instalowania programu Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Edytuj plik RegExLangServ.csproj (bez załadowanie go w programie Visual Studio.  
  
     W `Import` węzła, który odwołuje się do pliku Microsoft.VsSDK.targets Zastąp wartość z następującym tekstem.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Zapisz plik, a następnie zamknij go.  
  
4.  Otwórz rozwiązanie RegExLangServ.sln.  
  
5.  **Jednokierunkowe uaktualnienia** zostanie wyświetlone okno. Kliknij przycisk **OK**.  
  
6.  Aktualizowanie właściwości projektu. Otwórz **właściwości projektu** okna, wybierając węzeł projektu w **Eksploratora rozwiązań**, klikając prawym przyciskiem myszy i wybierając **właściwości**.  
  
    -   Na **aplikacji** Zmień **platformy docelowej** do **4.6.1**.  
  
    -   Na **debugowania** karcie **uruchomienia programu zewnętrznego** wpisz  **\<ścieżki instalacji programu Visual Studio > \Common7\IDE\devenv.exe.**.  
  
         W **argumenty wiersza polecenia** wpisz /**rootsuffix Exp**.  
  
7.  Zaktualizuj następujące informacje:  
  
    -   Usuń odwołanie do Microsoft.VisualStudio.Shell.9.0.dll, a następnie dodaj odwołania do Microsoft.VisualStudio.Shell.14.0.dll i Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Usuń odwołanie do Microsoft.VisualStudio.Package.LanguageService.9.0.dll, a następnie dodaj odwołanie do Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Otwórz plik VsPkg.cs i zmień wartość `DefaultRegistryRoot` atrybutu  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Należy dodać następujący atrybut do VsPkg.cs oryginalnej próbki nie rejestruje jej usługi języka.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Należy dodać pliku source.extension.vsixmanifest.  
  
    -   Skopiuj ten plik z rozszerzeniem istniejącej do katalogu projektu. (Jest jednym ze sposobów pobrać ten plik do tworzenia projektu VSIX (w obszarze **pliku**, kliknij przycisk **nowy**, następnie kliknij przycisk **projektu**. Kliknij w Visual Basic lub C# **rozszerzalności**, a następnie wybierz pozycję **projektu VSIX**.)  
  
    -   Dodaj plik do projektu.  
  
    -   W pliku **właściwości**ustaw **Akcja kompilacji** do **Brak**.  
  
    -   Otwórz plik z **Edytor manifestu VSIX**.  
  
    -   Zmień następujące pola:  
  
    -   **Identyfikator**: RegExLangServ  
  
    -   **Nazwa produktu**: RegExLangServ  
  
    -   **Opis elementu**: Usługa języka wyrażenia regularnego.  
  
    -   W obszarze **zasoby**, kliknij przycisk **nowy**, wybierz pozycję **typu** do **Microsoft.VisualStudio.VsPackage**ustaw **źródła** do **projekt w bieżącym rozwiązaniu**, a następnie ustaw **projektu** do **RegExLangServ**.  
  
    -   Zapisz i zamknij plik.  
  
11. Skompiluj rozwiązanie. Tworzenie plików są wdrażane na **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Rozpocznij debugowanie. Otworzyć drugie wystąpienie programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md)