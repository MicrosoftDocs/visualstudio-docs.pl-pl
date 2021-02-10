---
title: Wdrażanie niestandardowego procesora dyrektywy
description: Dowiedz się więcej o metodach dostępnych do wdrożenia niestandardowego procesora dyrektywy w programie Visual Studio lub na dowolnym komputerze.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dc839d4d859a8dd1dcc82774c466d6d103e4e7a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935342"
---
# <a name="deploying-a-custom-directive-processor"></a>Wdrażanie niestandardowego procesora dyrektywy

Aby użyć niestandardowego procesora dyrektywy w programie Visual Studio na dowolnym komputerze, należy zarejestrować go za pomocą jednej z metod opisanych w tym temacie.

Alternatywne metody to:

- [Rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Zapewnia to sposób zainstalowania i odinstalowywania procesora dyrektywy zarówno na swoim komputerze, jak i na innych komputerach. Zazwyczaj można umieścić inne funkcje w tym samym VSIX.

- [Pakietu VSPackage](../extensibility/internals/vspackages.md). W przypadku definiowania VSPackage, zawierającego inne funkcje oprócz procesora dyrektywy, istnieje wygodna metoda rejestracji procesora dyrektywy.

- Ustaw klucz rejestru. W tej metodzie należy dodać wpis rejestru dla procesora dyrektywy.

Musisz użyć jednej z tych metod tylko wtedy, gdy chcesz przekształcić szablon tekstowy w Visual Studio lub MSBuild. Jeśli używasz niestandardowego hosta w aplikacji, niestandardowy host jest odpowiedzialny za znalezienie procesorów dyrektyw dla każdej dyrektywy.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>Wdrażanie procesora dyrektywy w VSIX

Można dodać niestandardowy procesor dyrektywy do [rozszerzenia programu Visual Studio (VSIX)](../extensibility/starting-to-develop-visual-studio-extensions.md).

 Upewnij się, że w pliku .vsix znajdują się dwa następujące elementy:

- Zestaw (.dll), który zawiera niestandardową klasę procesora dyrektywy.

- Plik .pkgdef, który rejestruje procesor dyrektywy. Główna nazwa pliku musi być zgodna z nazwą zestawu. Na przykład, pliki mogą być nazwane CDP.dll i CDP.pkgdef.

Aby sprawdzić lub zmienić zawartość pliku .vsix, zmień rozszerzenie nazwy pliku na .zip, a następnie otwórz go. Po zakończeniu edycji zawartości zmień nazwę pliku z powrotem na .vsix.

Istnieje kilka sposobów tworzenia plików .vsix. Poniższa procedura opisuje jedną z metod.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Aby opracować niestandardowy procesor dyrektywy w projekcie VSIX

1. Utwórz nowy projekt **projektu VSIX** .

2. W polu **source. Extension. vsixmanifest** Ustaw typ zawartości i obsługiwane wersje.

    1. W edytorze manifestu VSIX na karcie **zasoby** wybierz pozycję **Nowy** i ustaw właściwości nowego elementu:

         **Typ zawartości**  =  **Pakietu VSPackage**

         **Projekt źródłowy** = \<*the current project*>

    2. Kliknij pozycję **wybrane wersje** i Sprawdź typy instalacji, na których ma być możliwe użycie procesora dyrektywy.

3. Dodaj plik .pkgdef i ustaw jego właściwości, które mają zostać uwzględnione w VSIX.

    1. Utwórz plik tekstowy i nadaj mu nazwę \<*assemblyName*> pkgdef.

         \<*assemblyName*> jest zwykle taka sama jak nazwa projektu.

    2. Wybierz go w oknie Eksploratora rozwiązań i ustaw jego właściwości w następujący sposób:

         **Akcja kompilacji**  =  **Zawartość**

         **Kopiuj do katalogu wyjściowego**  =  **Zawsze Kopiuj**

         **Uwzględnij w VSIX**  =  **Wartość true**

    3. Ustaw nazwę VSIX i upewnij się, że identyfikator jest unikatowy.

4. Dodaj następujący tekst do pliku .pkgdef.

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     Zastąp następujące nazwy własnymi nazwami: `CustomDirectiveProcessorName` , `NamespaceName` , `ClassName` , `AssemblyName` .

5. Dodaj następujące odwołania do projektu:

    - **Microsoft. VisualStudio. TextTemplating. \* . 2,0**

    - **Microsoft. VisualStudio. TextTemplating. Interfaces. \* . 2,0**

    - **Microsoft. VisualStudio. TextTemplating. VSHost. \* . 2,0**

6. Dodaj niestandardową klasę procesora dyrektywy do projektu.

     Jest to Klasa publiczna, która powinna implementować <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

#### <a name="to-install-the-custom-directive-processor"></a>Aby zainstalować procesor dyrektywy niestandardowej

1. W Eksploratorze Windows otwórz katalog kompilacji (zazwyczaj bin\Debug lub bin\Release).

2. Jeśli chcesz zainstalować procesor dyrektywy na innym komputerze, skopiuj plik .vsix do innego komputera.

3. Kliknij dwukrotnie plik .vsix. Zostanie wyświetlony Instalator rozszerzenia programu Visual Studio.

4. Uruchom ponownie program Visual Studio. Teraz można uruchomić szablony tekstowe, które zawierają dyrektywy odwołujące się do procesora dyrektywy niestandardowej. Każda dyrektywa jest tej postaci:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Aby odinstalować lub tymczasowo wyłączyć procesor dyrektywy niestandardowej

1. W menu **Narzędzia** programu Visual Studio kliknij pozycję **Menedżer rozszerzeń**.

2. Wybierz VSIX zawierający procesor dyrektywy, a następnie kliknij przycisk **Odinstaluj** lub **Wyłącz**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Rozwiązywanie problemów z procesorem dyrektywy w VSIX
 Jeśli procesor dyrektywy nie działa, poniższe sugestie mogą pomóc:

- Nazwa procesora określona w dyrektywie niestandardowej powinna być zgodna z `CustomDirectiveProcessorName` określoną w pliku. pkgdef.

- `IsDirectiveSupported`Metoda musi zwrócić `true` , gdy zostanie przeniesiona nazwa `CustomDirective` .

- Jeśli nie widzisz rozszerzenia w Menedżerze rozszerzeń, ale system nie zezwoli na jego instalację, Usuń rozszerzenie z **%LocalAppData%\Microsoft\VisualStudio \\ \* 0 \ Extensions \\**.

- Otwórz plik .vsix i sprawdź jego zawartość. Aby go otworzyć, zmień rozszerzenie nazwy pliku na .zip. Sprawdź, czy zawiera on pliki .dll, .pkgdef i extension.vsixmanifest. Plik extension.vsixmanifest powinien zawierać odpowiednią listę w węźle SupportedProducts i powinien też zawierać węzeł VsPackage w węźle Content:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Wdrażanie procesora dyrektywy w VSPackage
 Jeśli procesor dyrektywy jest częścią pakietu VSPackage, który zostanie zainstalowany w pamięci podręcznej GAC, system może automatycznie wygenerować plik .pkgdef.

 Umieść następujący atrybut w klasie pakietu:

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
> Ten atrybut jest umieszczany w klasie pakietu, a nie w klasie procesora dyrektywy.

 Plik .pkgdef zostanie wygenerowany podczas tworzenia projektu. Podczas instalowania pakietu VSPackage plik .pkgdef zarejestruje procesor dyrektywy.

 Sprawdź, czy plik .pkgdef pojawia się w folderze kompilacji, zwykle bin\Debug lub bin\Release. Jeśli nie jest wyświetlany, Otwórz plik. csproj w edytorze tekstu i usuń następujący węzeł: `<GeneratePkgDefFile>false</GeneratePkgDefFile>` .

 Aby uzyskać więcej informacji, zobacz [pakietów VSPackage](../extensibility/internals/vspackages.md).

## <a name="setting-a-registry-key"></a>Ustawianie klucza rejestru.
 Ta metoda instalacji procesora dyrektywy niestandardowej jest najmniej polecana. Nie zapewnia wygodnego sposobu włączania i wyłączania procesora dyrektywy i nie zapewnia metody dystrybucji procesora dyrektywy do innych użytkowników.

> [!CAUTION]
> Niewłaściwe edytowanie rejestru może poważnie uszkodzić system. Przed wprowadzeniem zmian w rejestrze należy wykonać kopię zapasową wszystkich cennych danych, które znajdują się na komputerze.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Aby zarejestrować procesor dyrektywy przez ustawienie klucza rejestru

1. Uruchom polecenie `regedit`.

2. W edytorze regedit przejdź do

    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ \* . 0 \ TextTemplating\DirectiveProcessors**

    Jeśli chcesz zainstalować procesor dyrektywy w eksperymentalnej wersji programu Visual Studio, Wstaw "EXP" po "11,0".

3. Dodaj klucz rejestru, który ma taką samą nazwę jak klasa procesora dyrektywy.

   - W drzewie rejestru kliknij prawym przyciskiem myszy węzeł **DirectiveProcessors** , wskaż polecenie **Nowy**, a następnie kliknij pozycję **klucz**.

4. W nowym węźle dodaj wartości ciągu dla Class i CodeBase lub Assembly, zgodnie z poniższymi tabelami.

   1. Kliknij prawym przyciskiem myszy utworzony węzeł, wskaż polecenie **Nowy**, a następnie kliknij pozycję **wartość ciągu**.

   2. Wyedytuj nazwę wartości.

   3. Kliknij dwukrotnie nazwę i wyedytuj dane.

   Jeśli procesor dyrektywy niestandardowej nie znajduje się w pamięci podręcznej GAC, podklucze rejestru powinny wyglądać tak, jak w poniższej tabeli:

|Nazwa|Typ|Dane|
|-|-|-|
|(Domyślnie)|REG_SZ|(wartość nieustawiona)|
|Klasa|REG_SZ|**\<Namespace Name>.\<Class Name>**|
|CodeBase|REG_SZ|**\<Your Path>\\<nazwę zestawu\>**|

 W przypadku zestawu w pamięci podręcznej GAC, podklucze rejestru powinny wyglądać tak, jak w poniższej tabeli:

|Nazwa|Typ|Dane|
|-|-|-|
|(Domyślnie)|REG_SZ|(wartość nieustawiona)|
|Klasa|REG_SZ|\<**Your Fully Qualified Class Name**>|
|Zestaw|REG_SZ|\<**Your Assembly Name in the GAC**>|

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego](../modeling/creating-custom-t4-text-template-directive-processors.md)
