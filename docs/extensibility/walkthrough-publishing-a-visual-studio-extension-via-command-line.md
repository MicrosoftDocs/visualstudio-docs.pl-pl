---
title: Publikowanie rozszerzenia przy użyciu wiersza polecenia
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5108f4afa382c00376424432d2086f0494e34a03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904676"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Przewodnik: Publikowanie rozszerzenia programu Visual Studio za pomocą wiersza polecenia

W tym instruktażu przedstawiono sposób publikowania rozszerzenia programu Visual Studio do Visual Studio Marketplace przy użyciu wiersza polecenia. Po dodaniu rozszerzenia do portalu Marketplace deweloperzy mogą skorzystać z okna dialogowego [**rozszerzenia i aktualizacje**](../ide/finding-and-using-visual-studio-extensions.md) , aby wyszukać nowe i zaktualizowane rozszerzenia.

VsixPublisher.exe jest narzędziem wiersza polecenia do publikowania rozszerzeń programu Visual Studio w portalu Marketplace. Dostęp do niego można uzyskać za pomocą $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Polecenia dostępne w tym narzędziu to **publish**: Publish **,** **deletePublisher**, **deleteExtension**, **login**, **Wyloguj**się.

## <a name="commands"></a>Polecenia

### <a name="publish"></a>publish

Publikuje rozszerzenie w portalu Marketplace. Rozszerzeniem może być plik VSIX, exe/MSI lub link. Jeśli rozszerzenie już istnieje w tej samej wersji, spowoduje zastąpienie rozszerzenia. Jeśli rozszerzenie jeszcze nie istnieje, zostanie utworzone nowe rozszerzenie.

|Opcje polecenia |Opis |
|---------|---------|
|ładunek (wymagany) | Ścieżka do ładunku do opublikowania lub linku, który ma być używany jako adres URL "więcej informacji". |
|publishManifest (wymagane) | Ścieżka do pliku manifestu publikowania do użycia. |
|ignoreWarnings | Lista ostrzeżeń do ignorowania podczas publikowania rozszerzenia. Te ostrzeżenia są wyświetlane jako komunikaty wiersza polecenia podczas publikowania rozszerzenia. (na przykład "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Osobisty token dostępu używany do uwierzytelniania wydawcy. Jeśli nie zostanie podany, zostanie uzyskana z zalogowanych użytkowników. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>Cofnij publikowanie

Tworzy wydawcę w portalu Marketplace. Rejestruje także wydawcę na komputerze w celu wykonania przyszłych akcji (na przykład usunięcie/opublikowanie rozszerzenia).

|Opcje polecenia |Opis |
|---------|---------|
|displayName (wymagane) | Nazwa wyświetlana wydawcy. |
|wydawcaname (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|personalAccessToken (wymagane) | Osobisty token dostępu używany do uwierzytelniania wydawcy. |
|shortDescription | Krótki opis wydawcy (nie plik). |
|longDescription | Długi opis wydawcy (nie plik). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Usuwa wydawcę w portalu Marketplace.

|Opcje polecenia |Opis |
|---------|---------|
|wydawcaname (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|personalAccessToken (wymagane) | Osobisty token dostępu używany do uwierzytelniania wydawcy. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Usuwa rozszerzenie z portalu Marketplace.

|Opcje polecenia |Opis |
|---------|---------|
|ExtensionName (wymagane) | Nazwa rozszerzenia do usunięcia. |
|wydawcaname (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|personalAccessToken | Osobisty token dostępu używany do uwierzytelniania wydawcy. Jeśli nie zostanie podany, zostanie uzyskana z zalogowanych użytkowników. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>logowanie

Rejestruje wydawcę na komputerze.

|Opcje polecenia |Opis |
|---------|---------|
|personalAccessToken (wymagane | Osobisty token dostępu używany do uwierzytelniania wydawcy. |
|wydawcaname (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|pisz | Określa, że istniejący Wydawca powinien zostać zastąpiony nowym osobistym tokenem dostępu. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Rejestruje wydawcę z komputera.

|Opcje polecenia |Opis |
|---------|---------|
|wydawcaname (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|ignoreMissingPublisher | Określa, że narzędzie nie powinno być błędem, jeśli określony wydawca nie jest jeszcze zalogowany. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>plik publishManifest

Plik publishManifest jest używany przez polecenie **Publikuj** . Reprezentuje wszystkie metadane dotyczące rozszerzenia, które musi znać witryna Marketplace. Jeśli przekazane rozszerzenie pochodzi z rozszerzenia VSIX, właściwość "Identity" musi mieć tylko ustawioną wartość "InternalName". Wynika to z faktu, że pozostałe właściwości "Identity" można generować z pliku vsixmanifest. Jeśli rozszerzenie jest rozszerzeniem msi/exe lub łączem, użytkownik musi podać wymagane pola we właściwości "Identity" (tożsamość). Pozostała część manifestu zawiera informacje specyficzne dla portalu Marketplace (na przykład kategorie, czy funkcja Q&A jest włączona itp.).

Przykład pliku publishManifest rozszerzenia VSIX:

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

Przykładowy plik MSI/EXE lub LINK publishManifest:

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

Pliki zasobów można dostarczyć do osadzania takich elementów jak obrazy w pliku Readme. Na przykład, jeśli rozszerzenie ma następujący dokument z promocji "przegląd":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

W celu rozpoznania "obrazów/testlogo.png" w poprzednim przykładzie użytkownik może podać "assetFiles" w swoim manifeście publikowania, jak poniżej:

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

## <a name="publishing-walkthrough"></a>Przewodnik po publikowaniu

### <a name="prerequisites"></a>Wymagania wstępne

Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Utwórz rozszerzenie programu Visual Studio

W takim przypadku zostanie użyte domyślne rozszerzenie pakietu VSPackage, ale te same kroki są prawidłowe dla każdego rodzaju rozszerzenia.

1. Utwórz element pakietu VSPackage w języku C# o nazwie "TestPublish", który ma polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie pierwszego rozszerzenia: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Pakowanie rozszerzenia

1. Zaktualizuj rozszerzenie VSIXMANIFEST o prawidłowe informacje o nazwie produktu, autorze i wersji.

   ![Aktualizacja rozszerzenia vsixmanifest](media/update-extension-vsixmanifest.png)

2. Kompiluj swoje rozszerzenie w trybie **wydania** . Teraz Twoje rozszerzenie zostanie spakowane jako VSIX w folderze \bin\Release.

3. Aby zweryfikować instalację, można kliknąć dwukrotnie VSIX.

### <a name="test-the-extension"></a>Testowanie rozszerzenia

 Przed rozpoczęciem dystrybucji rozszerzenia, skompiluj i przetestuj go, aby upewnić się, że jest prawidłowo zainstalowany w eksperymentalnym wystąpieniu programu Visual Studio.

1. W programie Visual Studio Rozpocznij debugowanie. , aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

2. W eksperymentalnym wystąpieniu przejdź do menu **Narzędzia** , a następnie kliknij pozycję **rozszerzenia i aktualizacje..**.. Rozszerzenie TestPublish powinno pojawić się w środkowym okienku i być włączone.

3. W menu **Narzędzia** upewnij się, że widzisz polecenie Test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publikowanie rozszerzenia w portalu Marketplace za pośrednictwem wiersza polecenia

1. Upewnij się, że masz wbudowaną wersję wydania rozszerzenia oraz że jest ona aktualna.

2. Upewnij się, że utworzono publishmanifest.jsw plikach i overview.md.

3. Otwórz wiersz polecenia i przejdź do katalogu $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Aby utworzyć nowego wydawcę, użyj następującego polecenia:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Po pomyślnym utworzeniu wydawcy zostanie wyświetlony następujący komunikat z wierszem polecenia:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Możesz zweryfikować utworzonego nowego wydawcę, przechodząc do [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Aby opublikować nowe rozszerzenie, użyj następującego polecenia:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Po pomyślnym utworzeniu wydawcy zostanie wyświetlony następujący komunikat z wierszem polecenia:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Możesz sprawdzić nowe rozszerzenie opublikowane przez przechodzenie do [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Zainstaluj rozszerzenie z Visual Studio Marketplace

Po opublikowaniu rozszerzenia zainstaluj je w programie Visual Studio i przetestuj je w tym miejscu.

1. W programie Visual Studio w menu **Narzędzia** kliknij polecenie **rozszerzenia i aktualizacje...**.

2. Kliknij pozycję **online** , a następnie wyszukaj ciąg TestPublish.

3. Kliknij pozycję **Pobierz**. Rozszerzenie zostanie zaplanowane do instalacji.

4. Aby ukończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuwanie rozszerzenia

Można usunąć rozszerzenie z Visual Studio Marketplace i z komputera.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Aby usunąć rozszerzenie z portalu Marketplace za pośrednictwem wiersza polecenia

1. Jeśli chcesz usunąć rozszerzenie, użyj następującego polecenia:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Po pomyślnym usunięciu rozszerzenia zostanie wyświetlony następujący komunikat z wierszem polecenia:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenie z komputera

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **rozszerzenia i aktualizacje**.

2. Wybierz pozycję "MyVsixExtension", a następnie kliknij przycisk **Odinstaluj**. Rozszerzenie zostanie zaplanowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
