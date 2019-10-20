---
title: Wdrażanie niestandardowego procesora dyrektywy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6cce0a918b1b3e029846176832ab2feb74e3e9e4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669835"
---
# <a name="deploying-a-custom-directive-processor"></a>Wdrażanie niestandardowego procesora dyrektywy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby użyć niestandardowego procesora dyrektywy w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na dowolnym komputerze, należy zarejestrować go za pomocą jednej z metod opisanych w tym temacie.

 Alternatywne metody to:

- [Rozszerzenie programu Visual Studio (VSIX)](https://msdn.microsoft.com/64ff1452-f7d5-42d9-98b8-76f769f76832). Zapewnia to sposób zainstalowania i odinstalowywania procesora dyrektywy zarówno na swoim komputerze, jak i na innych komputerach. Zazwyczaj można umieścić inne funkcje w tym samym VSIX.

- [Pakietu VSPackage](../extensibility/internals/vspackages.md). W przypadku definiowania VSPackage, zawierającego inne funkcje oprócz procesora dyrektywy, istnieje wygodna metoda rejestracji procesora dyrektywy.

- Ustaw klucz rejestru. W tej metodzie należy dodać wpis rejestru dla procesora dyrektywy.

  Musisz użyć jednej z następujących metod tylko wtedy, gdy chcesz przekształcić szablon tekstowy w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Jeśli używasz niestandardowego hosta w aplikacji, niestandardowy host jest odpowiedzialny za znalezienie procesorów dyrektyw dla każdej dyrektywy.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>Wdrażanie procesora dyrektywy w VSIX
 Można dodać niestandardowy procesor dyrektywy do [rozszerzenia programu Visual Studio (VSIX)](https://msdn.microsoft.com/64ff1452-f7d5-42d9-98b8-76f769f76832).

 Upewnij się, że w pliku .vsix znajdują się dwa następujące elementy:

- Zestaw (.dll), który zawiera niestandardową klasę procesora dyrektywy.

- Plik .pkgdef, który rejestruje procesor dyrektywy. Główna nazwa pliku musi być zgodna z nazwą zestawu. Na przykład, pliki mogą być nazwane CDP.dll i CDP.pkgdef.

  Aby sprawdzić lub zmienić zawartość pliku .vsix, zmień rozszerzenie nazwy pliku na .zip, a następnie otwórz go. Po zakończeniu edycji zawartości zmień nazwę pliku z powrotem na .vsix.

  Istnieje kilka sposobów tworzenia plików .vsix. Poniższa procedura opisuje jedną z metod.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>Aby opracować niestandardowy procesor dyrektywy w projekcie VSIX

1. Utwórz projekt VSIX w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

    - W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **Wizualizacja C#** , a następnie rozwiń węzeł **rozszerzalność**. Kliknij pozycję **Projekt VSIX**.

2. W polu **source. Extension. vsixmanifest**Ustaw typ zawartości i obsługiwane wersje.

    1. W edytorze manifestu VSIX na karcie **zasoby** wybierz pozycję **Nowy** i ustaw właściwości nowego elementu:

         **Typ zawartości**  = **pakietu VSPackage**

         **Projekt źródłowy**  =  \<*bieżącym projekcie* >

    2. Kliknij pozycję **wybrane wersje** i Sprawdź typy instalacji, na których ma być możliwe użycie procesora dyrektywy.

3. Dodaj plik .pkgdef i ustaw jego właściwości, które mają zostać uwzględnione w VSIX.

    1. Utwórz plik tekstowy i nadaj mu nazwę \<*assemblyName*>. pkgdef.

         \<*assemblyName*> jest zwykle taka sama jak nazwa projektu.

    2. Wybierz go w oknie Eksploratora rozwiązań i ustaw jego właściwości w następujący sposób:

         **Akcja kompilacji**  = **zawartość**

         **Kopiuj do katalogu wyjściowego**  = **Kopiuj zawsze**

         **Uwzględnij w VSIX**  = **true**

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

     Zastąp następujące nazwy własnymi nazwami: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName` `AssemblyName`.

5. Dodaj następujące odwołania do projektu:

    - **Microsoft. VisualStudio. TextTemplating. \*.0**

    - **Microsoft. VisualStudio. TextTemplating. Interfaces. \*.0**

    - **Microsoft. VisualStudio. TextTemplating. VSHost. \*.0**

6. Dodaj niestandardową klasę procesora dyrektywy do projektu.

     Jest to Klasa publiczna, która powinna implementować <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

#### <a name="to-install-the-custom-directive-processor"></a>Aby zainstalować procesor dyrektywy niestandardowej

1. W Eksploratorze Windows (Eksplorator plików w systemie Windows 8) otwórz katalog kompilacji (zazwyczaj bin\Debug lub bin\Release).

2. Jeśli chcesz zainstalować procesor dyrektywy na innym komputerze, skopiuj plik .vsix do innego komputera.

3. Kliknij dwukrotnie plik .vsix. Zostanie wyświetlony Instalator rozszerzenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Teraz można uruchomić szablony tekstowe, które zawierają dyrektywy odwołujące się do procesora dyrektywy niestandardowej. Każda dyrektywa jest tej postaci:

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" … #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>Aby odinstalować lub tymczasowo wyłączyć procesor dyrektywy niestandardowej

1. W menu **narzędzia** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kliknij pozycję **Menedżer rozszerzeń**.

2. Wybierz VSIX zawierający procesor dyrektywy, a następnie kliknij przycisk **Odinstaluj** lub **Wyłącz**.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>Rozwiązywanie problemów z procesorem dyrektywy w VSIX
 Jeśli procesor dyrektywy nie działa, poniższe sugestie mogą pomóc:

- Nazwa procesora określona w dyrektywie niestandardowej powinna być zgodna z `CustomDirectiveProcessorName`, który został określony w pliku. pkgdef.

- Metoda `IsDirectiveSupported` musi zwrócić `true`, gdy zostanie przeniesiona nazwa `CustomDirective`.

- Jeśli nie widzisz rozszerzenia w Menedżerze rozszerzeń, ale system nie zezwoli na jego instalację, Usuń rozszerzenie z **%localappdata%\Microsoft\VisualStudio \\ \* 0 \ Extensions \\** .

- Otwórz plik .vsix i sprawdź jego zawartość. Aby go otworzyć, zmień rozszerzenie nazwy pliku na .zip. Sprawdź, czy zawiera on pliki .dll, .pkgdef i extension.vsixmanifest. Plik extension.vsixmanifest powinien zawierać odpowiednią listę w węźle SupportedProducts i powinien też zawierać węzeł VsPackage w węźle Content:

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>Wdrażanie procesora dyrektywy w VSPackage
 Jeśli procesor dyrektywy jest częścią pakietu VSPackage, który zostanie zainstalowany w pamięci podręcznej GAC, system może automatycznie wygenerować plik .pkgdef.

 Umieść następujący atrybut w klasie pakietu:

```
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
> Ten atrybut jest umieszczany w klasie pakietu, a nie w klasie procesora dyrektywy.

 Plik .pkgdef zostanie wygenerowany podczas tworzenia projektu. Podczas instalowania pakietu VSPackage plik .pkgdef zarejestruje procesor dyrektywy.

 Sprawdź, czy plik .pkgdef pojawia się w folderze kompilacji, zwykle bin\Debug lub bin\Release. Jeśli nie jest wyświetlany, Otwórz plik. csproj w edytorze tekstu i usuń następujący węzeł: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.

 Aby uzyskać więcej informacji, zobacz [pakietów VSPackage](../extensibility/internals/vspackages.md).

## <a name="setting-a-registry-key"></a>Ustawianie klucza rejestru.
 Ta metoda instalacji procesora dyrektywy niestandardowej jest najmniej polecana. Nie zapewnia wygodnego sposobu włączania i wyłączania procesora dyrektywy i nie zapewnia metody dystrybucji procesora dyrektywy do innych użytkowników.

> [!CAUTION]
> Niepoprawne edytowanie rejestru może spowodować poważne uszkodzenie systemu. Przed wprowadzeniem zmian w rejestrze należy wykonać kopię zapasową wszystkich cennych danych, które znajdują się na komputerze.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>Aby zarejestrować procesor dyrektywy przez ustawienie klucza rejestru

1. Uruchom `regedit`.

2. W edytorze regedit przejdź do

    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ \*.0 \ TextTemplating\DirectiveProcessors**

    Jeśli chcesz zainstalować procesor dyrektywy w eksperymentalnej wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Wstaw "EXP" po "11,0".

3. Dodaj klucz rejestru, który ma taką samą nazwę jak klasa procesora dyrektywy.

   - W drzewie rejestru kliknij prawym przyciskiem myszy węzeł **DirectiveProcessors** , wskaż polecenie **Nowy**, a następnie kliknij pozycję **klucz**.

4. W nowym węźle dodaj wartości ciągu dla Class i CodeBase lub Assembly, zgodnie z poniższymi tabelami.

   1. Kliknij prawym przyciskiem myszy utworzony węzeł, wskaż polecenie **Nowy**, a następnie kliknij pozycję **wartość ciągu**.

   2. Wyedytuj nazwę wartości.

   3. Kliknij dwukrotnie nazwę i wyedytuj dane.

   Jeśli procesor dyrektywy niestandardowej nie znajduje się w pamięci podręcznej GAC, podklucze rejestru powinny wyglądać tak, jak w poniższej tabeli:

|Nazwa|Typ|Dane|
|----------|----------|----------|
|(Domyślnie)|REG_SZ|(wartość nieustawiona)|
|Class|REG_SZ|**> nazwy \<Namespace. Nazwa \<Class >**|
|CodeBase|REG_SZ|**Ścieżka \<Your > \\ < nazwą zestawu \>**|

 W przypadku zestawu w pamięci podręcznej GAC, podklucze rejestru powinny wyglądać tak, jak w poniższej tabeli:

|Nazwa|Typ|Dane|
|----------|----------|----------|
|(Domyślnie)|REG_SZ|(wartość nieustawiona)|
|Class|REG_SZ|\< w**pełni kwalifikowaną nazwę klasy** >|
|Zestaw|REG_SZ|\<**nazwę zestawu w pamięci PODręcznej GAC** >|

## <a name="see-also"></a>Zobacz też
 [Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego](../modeling/creating-custom-t4-text-template-directive-processors.md)
