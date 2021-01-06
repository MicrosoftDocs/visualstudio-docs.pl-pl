---
title: Migrowanie starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się, jak zaktualizować usługę języka do najnowszej wersji programu Visual Studio, aktualizując projekt i dodając plik source. Extension. vsixmanifest.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ced200ff24b17f312e63642c8083f038a6fc6a4d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877835"
---
# <a name="migrating-a-legacy-language-service"></a>Migrowanie starszej wersji usługi językowej
Starszą wersję usługi językowej można zmigrować do nowszej wersji programu Visual Studio przez zaktualizowanie projektu i dodanie pliku source. Extension. vsixmanifest do projektu. Sama usługa językowa będzie nadal działać tak jak wcześniej, ponieważ Edytor programu Visual Studio dostosowuje go.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi językowej, zobacz [edytory i rozszerzenia usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrowanie rozwiązania usługi językowej programu Visual Studio 2008 do nowszej wersji
 Poniższe kroki pokazują, jak dostosować przykład programu Visual Studio 2008 o nazwie RegExLanguageService. Ten przykład można znaleźć w instalacji programu Visual Studio 2008 SDK w folderze \VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ *ścieżka instalacji zestawu SDK programu Visual Studio*.

> [!IMPORTANT]
> Jeśli usługa języka nie definiuje kolorów, należy jawnie ustawić na <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` pakietu VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Aby przeprowadzić migrację usługi języka Visual Studio 2008 do nowszej wersji

1. Zainstaluj nowsze wersje programu Visual Studio i Visual Studio SDK. Aby uzyskać więcej informacji o sposobach instalowania zestawu SDK, zobacz [Instalowanie zestawu SDK programu Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).

2. Edytuj plik RegExLangServ. csproj (bez ładowania go w programie Visual Studio).

     W `Import` węźle, który odwołuje się do pliku Microsoft. VsSDK. targets, Zastąp wartość następującym tekstem.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Zapisz plik, a następnie zamknij go.

4. Otwórz rozwiązanie RegExLangServ. sln.

5. Zostanie wyświetlone okno **uaktualnianie jednokierunkowe** . Kliknij przycisk **OK**.

6. Zaktualizuj właściwości projektu. Otwórz okno **właściwości projektu** , wybierając węzeł projektu w **Eksplorator rozwiązań**, klikając prawym przyciskiem myszy i wybierając pozycję **Właściwości**.

    - Na karcie **aplikacja** Zmień **platformę docelową** na **4.6.1**.

    - Na karcie **debugowanie** w polu **początkowy program zewnętrzny** wpisz **\<Visual Studio installation path>\Common7\IDE\devenv.exe.**.

         W polu **argumenty wiersza polecenia** wpisz/**rootsuffix Exp**.

7. Zaktualizuj następujące odwołania:

    - Usuń odwołanie do Microsoft.VisualStudio.Shell.9.0.dll, a następnie Dodaj odwołania do Microsoft.VisualStudio.Shell.14.0.dll i Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Usuń odwołanie do Microsoft.VisualStudio.Package.LanguageService.9.0.dll, a następnie Dodaj odwołanie do Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Otwórz plik VsPkg.cs i zmień wartość `DefaultRegistryRoot` atrybutu na

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Oryginalny przykład nie rejestruje swojej usługi językowej, dlatego należy dodać następujący atrybut do VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Należy dodać plik source. Extension. vsixmanifest.

    - Skopiuj ten plik z istniejącego rozszerzenia do katalogu projektu. (Jednym ze sposobów uzyskania tego pliku jest utworzenie projektu VSIX (w obszarze **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt**. W obszarze Visual Basic lub C# kliknij **rozszerzalność**, a następnie wybierz **Projekt VSIX**.)

    - Dodaj plik do projektu.

    - We **właściwościach** pliku ustaw opcję **Akcja kompilacji** na **Brak**.

    - Otwórz plik z **edytorem manifestu VSIX**.

    - Zmień następujące pola:

    - **Identyfikator**: RegExLangServ

    - **Nazwa produktu**: RegExLangServ

    - **Opis**: Usługa języka wyrażeń regularnych.

    - W obszarze **zasoby** kliknij pozycję **Nowy**, wybierz **Typ** **Microsoft. VisualStudio. pakietu VSPackage**, ustaw **Źródło** na **projekt w bieżącym rozwiązaniu**, a następnie ustaw **projekt** na **RegExLangServ**.

    - Zapisz i zamknij plik.

11. Skompiluj rozwiązanie. Skompilowane pliki są wdrażane w usłudze **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ \\**.

12. Uruchom debugowanie. Zostało otwarte drugie wystąpienie programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md)
