---
title: Wdrażanie niestandardowego procesora dyrektywy
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba106bd28db63b6215abd02ea00aff0b3c0c00e0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432231"
---
# <a name="deploying-a-custom-directive-processor"></a>Wdrażanie niestandardowego procesora dyrektywy

Aby użyć niestandardowego procesora dyrektywy w programie Visual Studio na dowolnym komputerze, należy zarejestrować go za pomocą jednej z metod opisanych w tym temacie.

Alternatywne metody to:

- [Rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Zapewnia to sposób zainstalowania i odinstalowywania procesora dyrektywy zarówno na swoim komputerze, jak i na innych komputerach. Zazwyczaj można umieścić inne funkcje w tym samym VSIX.

- [Pakietu VSPackage](../extensibility/internals/vspackages.md). W przypadku definiowania VSPackage, zawierającego inne funkcje oprócz procesora dyrektywy, istnieje wygodna metoda rejestracji procesora dyrektywy.

- Ustaw klucz rejestru. W tej metodzie należy dodać wpis rejestru dla procesora dyrektywy.

Należy użyć jednej z następujących metod tylko wtedy, gdy chcesz przekształcić szablon tekstu w programie Visual Studio lub programu MSBuild. Jeśli używasz niestandardowego hosta w aplikacji, niestandardowy host jest odpowiedzialny za znalezienie procesorów dyrektyw dla każdej dyrektywy.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>Wdrażanie procesora dyrektywy w VSIX

Można dodać niestandardowy procesor dyrektywy do [rozszerzeniu Visual Studio (VSIX)](../extensibility/starting-to-develop-visual-studio-extensions.md).

 Upewnij się, że w pliku .vsix znajdują się dwa następujące elementy:

- Zestaw (.dll), który zawiera niestandardową klasę procesora dyrektywy.

- Plik .pkgdef, który rejestruje procesor dyrektywy. Główna nazwa pliku musi być zgodna z nazwą zestawu. Na przykład, pliki mogą być nazwane CDP.dll i CDP.pkgdef.

Aby sprawdzić lub zmienić zawartość pliku .vsix, zmień rozszerzenie nazwy pliku na .zip, a następnie otwórz go. Po zakończeniu edycji zawartości zmień nazwę pliku z powrotem na .vsix.

Istnieje kilka sposobów tworzenia plików .vsix. Poniższa procedura opisuje jedną z metod.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Aby opracować niestandardowy procesor dyrektywy w projekcie VSIX

1. Utwórz nową **projekt VSIX** projektu.

2. W **source.extension.vsixmanifest**, Ustaw typ zawartości i obsługiwane wersje.

    1. W pliku VSIX edytorze manifestu, na **zasoby** kartę, wybrać **New** i ustaw właściwości nowego elementu:

         **Typ zawartości** = **pakietu VSPackage**

         **Projekt źródła** = \<*bieżącego projektu*>

    2. Kliknij przycisk **wybrane wersje** i Sprawdź typy instalacji, na których chcesz mieć działający procesor dyrektywy.

3. Dodaj plik .pkgdef i ustaw jego właściwości, które mają zostać uwzględnione w VSIX.

    1. Utwórz plik tekstowy i nadaj mu nazwę \< *assemblyName*> .pkgdef.

         \<*assemblyName*> jest zwykle taka sama jak nazwa projektu.

    2. Wybierz go w oknie Eksploratora rozwiązań i ustaw jego właściwości w następujący sposób:

         **Akcja kompilacji** = **zawartości**

         **Kopiuj do katalogu wyjściowego** = **zawsze Kopiuj**

         **Uwzględnione w VSIX** = **True**

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

     Zastąp następujące nazwy własnymi nazwami: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.

5. Dodaj następujące odwołania do projektu:

    - **Microsoft.VisualStudio.TextTemplating.\*.0**

    - **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**

    - **Microsoft.VisualStudio.TextTemplating.VSHost.\*.0**

6. Dodaj niestandardową klasę procesora dyrektywy do projektu.

     To jest klasa publiczna, która powinna implementować <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

#### <a name="to-install-the-custom-directive-processor"></a>Aby zainstalować procesor dyrektywy niestandardowej

1. W Eksploratorze Windows otwórz katalog kompilacji (zazwyczaj bin\Debug lub bin\Release).

2. Jeśli chcesz zainstalować procesor dyrektywy na innym komputerze, skopiuj plik .vsix do innego komputera.

3. Kliknij dwukrotnie plik .vsix. Zostanie wyświetlony Instalator rozszerzenia programu Visual Studio.

4. Uruchom ponownie program Visual Studio. Teraz można uruchomić szablony tekstowe, które zawierają dyrektywy odwołujące się do procesora dyrektywy niestandardowej. Każda dyrektywa jest tej postaci:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Aby odinstalować lub tymczasowo wyłączyć procesor dyrektywy niestandardowej

1. W programie Visual Studio **narzędzia** menu, kliknij przycisk **Menedżera rozszerzeń**.

2. Wybierz VSIX zawierający procesor dyrektywy, a następnie kliknij przycisk **Odinstaluj** lub **wyłączyć**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Rozwiązywanie problemów z procesorem dyrektywy w VSIX
 Jeśli procesor dyrektywy nie działa, poniższe sugestie mogą pomóc:

- Nazwa procesora, którą określasz w niestandardowej dyrektywie powinna odpowiadać `CustomDirectiveProcessorName` określone w pliku .pkgdef.

- Twoje `IsDirectiveSupported` metoda musi zwracać `true` kiedy jest przekazywana nazwa sieci `CustomDirective`.

- Jeśli nie widzisz rozszerzenia w Menedżerze rozszerzeń, ale system nie pozwoli go zainstalować, usuń rozszerzenie z **%localappdata%\Microsoft\VisualStudio\\\*. 0\Extensions\\** .

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

 Sprawdź, czy plik .pkgdef pojawia się w folderze kompilacji, zwykle bin\Debug lub bin\Release. Jeśli nie zostanie wyświetlony, otwórz plik .csproj w edytorze tekstu i usuń następujący węzeł: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.

 Aby uzyskać więcej informacji, zobacz [pakietów VSPackage](../extensibility/internals/vspackages.md).

## <a name="setting-a-registry-key"></a>Ustawianie klucza rejestru.
 Ta metoda instalacji procesora dyrektywy niestandardowej jest najmniej polecana. Nie zapewnia wygodnego sposobu włączania i wyłączania procesora dyrektywy i nie zapewnia metody dystrybucji procesora dyrektywy do innych użytkowników.

> [!CAUTION]
> Niepoprawne edytowanie rejestru może spowodować poważne uszkodzenie systemu. Przed wprowadzeniem zmian w rejestrze należy wykonać kopię zapasową wszystkich cennych danych, które znajdują się na komputerze.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Aby zarejestrować procesor dyrektywy przez ustawienie klucza rejestru

1. Uruchom `regedit`.

2. W edytorze regedit przejdź do

    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**

    Jeśli chcesz zainstalować procesor dyrektywy w wersji doświadczalnej programu Visual Studio, Wstaw "Exp" po "11.0".

3. Dodaj klucz rejestru, który ma taką samą nazwę jak klasa procesora dyrektywy.

   - W drzewie rejestru kliknij prawym przyciskiem myszy **DirectiveProcessors** węzła, wskaż **New**, a następnie kliknij przycisk **klucz**.

4. W nowym węźle dodaj wartości ciągu dla Class i CodeBase lub Assembly, zgodnie z poniższymi tabelami.

   1. Kliknij prawym przyciskiem myszy węzeł, który został utworzony, wskaż opcję **New**, a następnie kliknij przycisk **wartość ciągu**.

   2. Wyedytuj nazwę wartości.

   3. Kliknij dwukrotnie nazwę i wyedytuj dane.

   Jeśli procesor dyrektywy niestandardowej nie znajduje się w pamięci podręcznej GAC, podklucze rejestru powinny wyglądać tak, jak w poniższej tabeli:

|Nazwa|Typ|Dane|
|-|-|-|
|(Domyślnie)|REG_SZ|(wartość nieustawiona)|
|Class|REG_SZ|**\<Nazwa Namespace >. \<Nazwa klasy >**|
|CodeBase|REG_SZ|**\<Twoja ścieżka >\\< Twoja nazwa zestawu\>**|

 W przypadku zestawu w pamięci podręcznej GAC, podklucze rejestru powinny wyglądać tak, jak w poniższej tabeli:

|Nazwa|Typ|Dane|
|-|-|-|
|(Domyślnie)|REG_SZ|(wartość nieustawiona)|
|Class|REG_SZ|\<**Usługi w pełni kwalifikowaną nazwę klasy**>|
|Zestaw|REG_SZ|\<**Twoja nazwa zestawu w GAC**>|

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego](../modeling/creating-custom-t4-text-template-directive-processors.md)