---
title: Publikowanie rozszerzenia przy użyciu wiersza polecenia
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697127"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Instruktaż: Publikowanie rozszerzenia programu Visual Studio za pomocą wiersza polecenia

W tym przewodniku pokazano, jak opublikować rozszerzenie programu Visual Studio do portalu Visual Studio Marketplace przy użyciu wiersza polecenia. Po dodaniu rozszerzenia do portalu Marketplace deweloperzy mogą używać okna dialogowego [**Rozszerzenia i aktualizacje,**](../ide/finding-and-using-visual-studio-extensions.md) aby przeglądać nowe i zaktualizowane rozszerzenia.

VsixPublisher.exe jest narzędziem wiersza polecenia do publikowania rozszerzeń programu Visual Studio w portalu Marketplace. Dostęp do niego można uzyskać z pliku ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Polecenia dostępne w tym narzędziu to: **publikuj**, **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **wyloguj się.**

## <a name="commands"></a>Polecenia

### <a name="publish"></a>publish

Publikuje rozszerzenie do portalu Marketplace. Rozszerzenie może być vsix, plik exe/msi lub łącze. Jeśli rozszerzenie już istnieje z tą samą wersją, zastąpi rozszerzenie. Jeśli rozszerzenie jeszcze nie istnieje, utworzy nowe rozszerzenie.

|Opcje poleceń |Opis |
|---------|---------|
|ładowność (wymagana) | Ścieżka do ładunku do opublikowania lub łącze do użycia jako "więcej informacji URL". |
|publishManifest (wymagane) | Ścieżka do pliku manifestu publikowania do użycia. |
|ignor ignoreWarnings ignoreWarnings ignoreWarnings ignore | Lista ostrzeżeń do zignorowania podczas publikowania rozszerzenia. Ostrzeżenia te są wyświetlane jako komunikaty wiersza polecenia podczas publikowania rozszerzenia. (na przykład "VSIXValidatorWarning01, VSIXValidatorWarning02")
|osobisteAccessToken | Osobisty token dostępu (PAT), który jest używany do uwierzytelniania wydawcy. Jeśli nie podano, PAT jest nabywany od zalogowanych użytkowników. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>utwórPublisher

Tworzy wydawcę w marketplace. Rejestruje również wydawcę na komputerze w celu przyszłych akcji (na przykład usunięcie/opublikowanie rozszerzenia).

|Opcje poleceń |Opis |
|---------|---------|
|displayName (wymagane) | Wyświetlana nazwa wydawcy. |
|publisherName (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|personalAccessToken (wymagane) | Osobisty token dostępu, który jest używany do uwierzytelniania wydawcy. |
|krótkiOskrypt | Krótki opis wydawcy (nie plik). |
|longDescription (opis) | Długi opis wydawcy (nie plik). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>usuńPublisher

Usuwa wydawcę w Marketplace.

|Opcje poleceń |Opis |
|---------|---------|
|publisherName (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|personalAccessToken (wymagane) | Osobisty token dostępu, który jest używany do uwierzytelniania wydawcy. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteWysoki

Usuwa rozszerzenie z marketplace.

|Opcje poleceń |Opis |
|---------|---------|
|extensionName (wymagane) | Nazwa rozszerzenia do usunięcia. |
|publisherName (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|osobisteAccessToken | Osobisty token dostępu, który jest używany do uwierzytelniania wydawcy. Jeśli nie podano, pat jest nabywany od zalogowanych użytkowników. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>logowanie

Rejestruje wydawcę na komputerze.

|Opcje poleceń |Opis |
|---------|---------|
|personalAccessToken (wymagane | Osobisty token dostępu, który jest używany do uwierzytelniania wydawcy. |
|publisherName (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|Zastąpić | Określa, że każdy istniejący wydawca powinien zostać zastąpiony nowym tokenem dostępu osobistego. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Rejestruje wydawcę z komputera.

|Opcje poleceń |Opis |
|---------|---------|
|publisherName (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|ignoreMissingPublisher | Określa, że narzędzie nie powinno być błędem, jeśli określony wydawca nie jest jeszcze zalogowany. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>pubManifest plik

Plik publishManifest jest używany przez polecenie **publikowania.** Reprezentuje wszystkie metadane dotyczące rozszerzenia, które marketplace musi wiedzieć. Jeśli przekazywane rozszerzenie pochodzi z rozszerzenia VSIX, właściwość "identity" musi mieć tylko zestaw "internalName". Dzieje się tak, ponieważ pozostałe właściwości "tożsamości" mogą być generowane z pliku vsixmanifest. Jeśli rozszerzenie jest msi/exe lub rozszerzenie łącza, użytkownik musi podać wymagane pola we właściwości "tożsamość". Pozostała część manifestu zawiera informacje specyficzne dla portalu Marketplace (na przykład kategorie, czy Q&A jest włączone itp.).

rozszerzenie VSIX publishPróbka plikuManifest:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE lub LINK publishPróbka plikuManifest:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Pliki zasobów

Pliki zasobów mogą być dostarczane do osadzania takich rzeczy rzeczy jak obrazy w pliku readme. Na przykład, jeśli rozszerzenie ma następujący dokument "przegląd" Markdown:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Aby rozwiązać "images/testlogo.png" w poprzednim przykładzie, użytkownik może podać "assetFiles" w ich manifest publikowania, jak poniżej:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Opublikowanie przewodnika

### <a name="prerequisites"></a>Wymagania wstępne

Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Tworzenie rozszerzenia programu Visual Studio

W takim przypadku użyjemy domyślnego rozszerzenia VSPackage, ale te same kroki są prawidłowe dla każdego rodzaju rozszerzenia.

1. Utwórz VSPackage w języku C# o nazwie "TestPublish", który ma polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie pierwszego rozszerzenia: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Pakiet rozszerzenia

1. Zaktualizuj rozszerzenie vsixmanifest z poprawnymi informacjami o nazwie produktu, autorze i wersji.

   ![rozszerzenie aktualizacji vsixmanifest](media/update-extension-vsixmanifest.png)

2. Tworzenie rozszerzenia w trybie **wydania.** Teraz rozszerzenie zostanie spakowane jako VSIX w folderze \bin\Release.

3. Można kliknąć dwukrotnie VSIX, aby zweryfikować instalację.

### <a name="test-the-extension"></a>Testowanie rozszerzenia

 Przed rozpowszechnieniem rozszerzenia, kompilacji i przetestować go, aby upewnić się, że jest poprawnie zainstalowany w eksperymentalnym wystąpieniu programu Visual Studio.

1. W programie Visual Studio rozpocznij debugowanie. , aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

2. W przypadku wystąpienia eksperymentalnego przejdź do menu **Narzędzia** i kliknij polecenie **Rozszerzenia i aktualizacje...**. Rozszerzenie TestPublish powinno pojawić się w środkowym okienku i być włączone.

3. W menu **Narzędzia** upewnij się, że jest widoczne polecenie testu.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publikowanie rozszerzenia w portalu Marketplace za pomocą wiersza polecenia

1. Upewnij się, że została skonstowana wersja wersji rozszerzenia i że jest aktualna.

2. Upewnij się, że utworzono pliki publishmanifest.json i overview.md.

3. Otwórz wiersz polecenia i przejdź do katalogu ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Aby utworzyć nowego wydawcę, użyj następującego polecenia:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Po pomyślnym utworzeniu wydawcy zostanie wyświetlony następujący komunikat wiersza polecenia:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Nowy wydawca został utworzony, przechodząc do [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Aby opublikować nowe rozszerzenie, użyj następującego polecenia:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Po pomyślnym utworzeniu wydawcy zostanie wyświetlony następujący komunikat wiersza polecenia:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Opublikowane rozszerzenie można zweryfikować, przechodząc do [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instalowanie rozszerzenia z portalu Visual Studio Marketplace

Teraz, gdy rozszerzenie zostanie opublikowane, zainstaluj je w programie Visual Studio i przetestuj je tam.

1. W programie Visual Studio w menu **Narzędzia** kliknij polecenie **Rozszerzenia i aktualizacje...**.

2. Kliknij **pozycję Online,** a następnie wyszukaj pozycję TestPublish.

3. Kliknij **pozycję Pobierz**. Rozszerzenie zostanie zaplanowane do zainstalowania.

4. Aby zakończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuwanie rozszerzenia

Rozszerzenie można usunąć z witryny Visual Studio Marketplace i z komputera.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Aby usunąć rozszerzenie z portalu Marketplace za pomocą wiersza polecenia

1. Jeśli chcesz usunąć rozszerzenie, użyj następującego polecenia:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Po pomyślnym usunięciu rozszerzenia zostanie wyświetlony następujący komunikat wiersza polecenia:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenie z komputera

1. W programie Visual Studio w menu **Narzędzia** kliknij polecenie **Rozszerzenia i aktualizacje**.

2. Wybierz "MyVsixExtension", a następnie kliknij przycisk **Odinstaluj**. Rozszerzenie zostanie następnie zaplanowane do odinstalowania.

3. Aby zakończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
