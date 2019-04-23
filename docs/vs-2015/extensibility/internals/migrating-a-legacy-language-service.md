---
title: Migrowanie starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe6870046d1dd15c7bc5795dd82d393272ca6b1e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097365"
---
# <a name="migrating-a-legacy-language-service"></a>Migrowanie starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aktualizowanie projektu i dodawanie pliku source.extension.vsixmanifest w projekcie, można migrować starszej wersji usługi językowej do nowszej wersji programu Visual Studio. Sama usługa języka będzie działać tak jak poprzednio, ponieważ w edytorze programu Visual Studio dostosowuje go.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi języka, zobacz [edytora i rozszerzenia usługi w języka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrowanie Visual Studio 2008 języka rozwiązanie typu Usługa do nowszej wersji.  
 Poniższe kroki pokazują jak dostosować o nazwie RegExLanguageService przykład programu Visual Studio 2008. W tym przykładzie w przypadku instalacji programu Visual Studio 2008 SDK można znaleźć w *ścieżka instalacji programu Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ folderu.  
  
> [!IMPORTANT]
>  Jeśli Twoja usługa języka nie definiuje kolory, musisz jawnie ustawić <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> do `true` na pakietu VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Aby przeprowadzić migrację usługi językowej programu Visual Studio 2008 do nowszej wersji.  
  
1. Zainstalować nowsze wersje programu Visual Studio i Visual Studio SDK. Aby uzyskać więcej informacji na temat sposobów instalowania zestawu SDK, zobacz [instalowania programu Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2. Edytuj plik RegExLangServ.csproj (bez załadowanie go w programie Visual Studio.  
  
     W `Import` węzeł, który odwołuje się do pliku Microsoft.VsSDK.targets, zastąp wartość symbolu następujący tekst.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3. Zapisz plik, a następnie zamknij go.  
  
4. Otwórz rozwiązanie RegExLangServ.sln.  
  
5. **Jednokierunkowe uaktualnienie** zostanie wyświetlone okno. Kliknij przycisk **OK**.  
  
6. Aktualizowanie właściwości projektu. Otwórz **właściwości projektu** okna, wybierając węzeł projektu w **Eksploratora rozwiązań**, kliknąć prawym przyciskiem myszy i wybierając opcję **właściwości**.  
  
    - Na **aplikacji** kartę, zmień **platformę docelową** do **4.6.1**.  
  
    - Na **debugowania** na karcie **uruchomienia programu zewnętrznego** wpisz  **\<ścieżka instalacji programu Visual Studio > \Common7\IDE\devenv.exe.**.  
  
         W **argumenty wiersza polecenia** wpisz /**rootsuffix Exp**.  
  
7. Zaktualizuj następujące informacje:  
  
    - Usuń odwołanie do Microsoft.VisualStudio.Shell.9.0.dll, a następnie dodać odwołania do Microsoft.VisualStudio.Shell.14.0.dll i Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    - Usuń odwołanie do Microsoft.VisualStudio.Package.LanguageService.9.0.dll, a następnie dodaj odwołanie do Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    - Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8. Otwórz plik VsPkg.cs i zmień wartość właściwości `DefaultRegistryRoot` atrybutu  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Oryginalnego przykładu nie rejestruje jej usługi języka, więc należy dodać następujący atrybut do VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Należy dodać plik source.extension.vsixmanifest.  
  
    - Skopiuj ten plik z rozszerzeniem istniejącej do katalogu projektu. (Utwórz projekt VSIX jest jednym ze sposobów przekazania tego pliku (w obszarze **pliku**, kliknij przycisk **New**, następnie kliknij przycisk **projektu**. Kliknij w języku Visual Basic lub C# **rozszerzalności**, a następnie wybierz **projekt VSIX**.)  
  
    - Dodaj plik do projektu.  
  
    - W pliku **właściwości**ustaw **Build Action** do **Brak**.  
  
    - Otwórz plik przy użyciu **edytorze manifestu VSIX**.  
  
    - Zmień następujące pola:  
  
    - **ID**: RegExLangServ  
  
    - **Nazwa produktu**: RegExLangServ  
  
    - **Opis**: Usługa języka wyrażeń regularnych.  
  
    - W obszarze **zasoby**, kliknij przycisk **New**, wybierz opcję **typu** do **Microsoft.VisualStudio.VsPackage**ustaw **źródła** do **projekt w bieżącym rozwiązaniu**, a następnie ustaw **projektu** do **RegExLangServ**.  
  
    - Zapisz i zamknij plik.  
  
11. Skompiluj rozwiązanie. Tworzenie plików są wdrażane w **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Rozpocznij debugowanie. Drugie wystąpienie programu Visual Studio jest otwarty.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md)
