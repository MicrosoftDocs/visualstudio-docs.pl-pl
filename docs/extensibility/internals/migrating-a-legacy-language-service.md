---
title: Migrowanie starszej usługi językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707111"
---
# <a name="migrating-a-legacy-language-service"></a>Migrowanie starszej wersji usługi językowej
Usługę starszego języka można przeprowadzić z migracją do nowszej wersji programu Visual Studio, aktualizując projekt i dodając plik source.extension.vsixmanifest do projektu. Sama usługa języka będzie nadal działać tak jak poprzednio, ponieważ edytor programu Visual Studio dostosowuje ją.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrowanie rozwiązania usługi językowej programu Visual Studio 2008 do nowszej wersji
 Poniższe kroki pokazują, jak dostosować przykład programu Visual Studio 2008 o nazwie RegExLanguageService. Ten przykład można znaleźć w instalacji SDK programu Visual Studio 2008 w *ścieżce instalacji zestawów SDK programu Visual Studio*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\folderu.

> [!IMPORTANT]
> Jeśli usługa języka nie definiuje kolorów, należy <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` jawnie ustawić na VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Aby przeprowadzić migrację usługi języka Visual Studio 2008 do nowszej wersji

1. Zainstaluj nowsze wersje programu Visual Studio i pakietu Visual Studio SDK. Aby uzyskać więcej informacji na temat sposobów instalowania zestawu SDK, zobacz [Instalowanie zestawu SDK programu Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).

2. Edytuj plik RegExLangServ.csproj (bez ładowania go w programie Visual Studio.

     W `Import` węźle, który odwołuje się do pliku Microsoft.VsSDK.targets, zastąp wartość następującym tekstem.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Zapisz plik, a następnie zamknij go.

4. Otwórz rozwiązanie RegExLangServ.sln.

5. Zostanie wyświetlone okno **uaktualnienia jednokierunkowego.** Kliknij przycisk **OK**.

6. Zaktualizuj właściwości projektu. Otwórz okno **Właściwości projektu,** zaznaczając węzeł projektu w **Eksploratorze rozwiązań,** klikając prawym przyciskiem myszy i wybierając polecenie **Właściwości**.

    - Na karcie **Aplikacja** zmień **strukturę docelową** na **4.6.1**.

    - Na karcie **Debugowanie** w polu **Uruchamianie programu zewnętrznego** wpisz ** \<ścieżkę instalacji programu Visual Studio>\Common7\IDE\devenv.exe.**.

         W polu **Argumenty wiersza polecenia** wpisz **/rootsuffix Exp**.

7. Zaktualizuj następujące odwołania:

    - Usuń odwołanie do pliku Microsoft.VisualStudio.Shell.9.0.dll, a następnie dodaj odwołania do pliku Microsoft.VisualStudio.Shell.14.0.dll i Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Usuń odwołanie do pliku Microsoft.VisualStudio.Package.LanguageService.9.0.dll, a następnie dodaj odwołanie do pliku Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Dodaj odwołanie do pliku Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Otwórz plik VsPkg.cs i zmień wartość `DefaultRegistryRoot` atrybutu na

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Oryginalny przykład nie rejestruje jego usługi języka, więc należy dodać następujący atrybut do VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Musisz dodać plik source.extension.vsixmanifest.

    - Skopiuj ten plik z istniejącego rozszerzenia do katalogu projektu. (Jednym ze sposobów uzyskania tego pliku jest utworzenie projektu VSIX (w obszarze **Plik**kliknij pozycję **Nowy**, a następnie kliknij pozycję **Projekt**. W obszarze Visual Basic lub C# kliknij pozycję **Rozszerzalność**, a następnie wybierz pozycję **VSIX Project**.)

    - Dodaj plik do projektu.

    - We **właściwościach**pliku ustaw **akcję kompilacji** na **Brak**.

    - Otwórz plik za pomocą **Edytora manifestów VSIX**.

    - Zmień następujące pola:

    - **ID**: RegExLangServ

    - **Nazwa produktu**: RegExLangServ

    - **Opis**: Usługa języka wyrażeń regularnych.

    - W obszarze **Zasoby**kliknij pozycję **Nowy**, wybierz **typ** do **Microsoft.VisualStudio.VsPackage**, ustaw **projekt Źródło** na A w **bieżącym rozwiązaniu**, a następnie ustaw **projekt** na **RegExLangServ**.

    - Zapisz i zamknij plik.

11. Skompiluj rozwiązanie. Wbudowane pliki są wdrażane w **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.

12. Rozpocznij debugowanie. Otwarto drugie wystąpienie programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md)
