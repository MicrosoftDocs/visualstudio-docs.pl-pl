---
title: Publikowanie rozszerzenia przy użyciu wiersza polecenia
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6b5531bc5dc138f2f90a0a67da39f9583bc4b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320649"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Przewodnik: Publikowanie rozszerzenia programu Visual Studio za pomocą wiersza polecenia

W tym instruktażu dowiesz się, jak opublikować rozszerzenia programu Visual Studio do witryny Marketplace programu Visual Studio przy użyciu wiersza polecenia. Po dodaniu rozszerzenia w portalu Marketplace, deweloperzy mogą używać [ **rozszerzenia i aktualizacje** ](../ide/finding-and-using-visual-studio-extensions.md) okno dialogowe wyszukiwania istnieje nowe i zaktualizowane rozszerzenia.

VsixPublisher.exe to narzędzie wiersza polecenia do publikowania rozszerzenia programu Visual Studio w witrynie Marketplace. Są dostępne z ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Są dostępne w tym narzędzia polecenia: **publikowania**, **createPublisher**, **deletePublisher**, **deleteExtension**,  **Zaloguj się**, **wylogowania**.

## <a name="commands"></a>Polecenia

### <a name="publish"></a>Publikowanie

Publikuje rozszerzenia w portalu Marketplace. Rozszerzenie może być vsix, plik exe/msi lub łącza. Jeśli rozszerzenie jest już w tej samej wersji, zastąpi rozszerzenia. Jeśli rozszerzenie nie istnieje, utworzy nowe rozszerzenie.

|Opcje polecenia |Opis |
|---------|---------|
|ładunek (wymagane) | Albo ścieżka do ładunku do opublikowania lub link do użycia jako "Więcej informacji o adres URL". |
|publishManifest (wymagane) | Ścieżka do publikowania manifestu plik do użycia. |
|ignoreWarnings | Lista ostrzeżeń do zignorowania podczas publikowania rozszerzenia. Ostrzeżenia te są wyświetlane jako komunikaty wiersza polecenia przy publikowaniu rozszerzeniem. (na przykład "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Osobiste Token dostępu (PAT), który jest używany do uwierzytelniania wydawcy. Jeśli nie zostanie podana, osobisty token dostępu jest uzyskanych z zalogowanych użytkowników. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Tworzy wydawcy w portalu Marketplace. Na komputerze dla przyszłych akcji (na przykład, usunięcie/publikowanie rozszerzenia) rejestruje wydawcy.

|Opcje polecenia |Opis |
|---------|---------|
|Nazwa wyświetlana (wymagane) | Nazwa wyświetlana wydawcy. |
|Nazwa_wydawcy (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|personalAccessToken (wymagane) | Osobisty Token dostępu, który jest używany do uwierzytelniania wydawcy. |
|shortDescription | Krótki opis wydawcy (nie plik). |
|longDescription | Długi opis wydawcy (nie plik). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Usuwa wydawcy w portalu Marketplace.

|Opcje polecenia |Opis |
|---------|---------|
|Nazwa_wydawcy (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|personalAccessToken (wymagane) | Osobisty Token dostępu, który jest używany do uwierzytelniania wydawcy. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Usuwa rozszerzenie z witryny Marketplace.

|Opcje polecenia |Opis |
|---------|---------|
|extensionName (wymagane) | Nazwa rozszerzenia do usunięcia. |
|Nazwa_wydawcy (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|personalAccessToken | Osobisty Token dostępu, który jest używany do uwierzytelniania wydawcy. Jeśli nie zostanie podana, osobisty token dostępu jest uzyskanych z zalogowanych użytkowników. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>Zaloguj się

Wydawca loguje się do komputera.

|Opcje polecenia |Opis |
|---------|---------|
|personalAccessToken (wymagane | Osobisty Token dostępu, który jest używany do uwierzytelniania wydawcy. |
|Nazwa_wydawcy (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|Zastąp | Określa, że wszelkie istniejącego wydawcę powinny być zastąpione przy użyciu nowego osobisty token dostępu. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>Wyloguj

Rejestruje wydawcy z komputera.

|Opcje polecenia |Opis |
|---------|---------|
|Nazwa_wydawcy (wymagane) | Nazwa wydawcy (na przykład identyfikator). |
|ignoreMissingPublisher | Określa, że narzędzie powinien błędu, jeśli określony wydawca są nie już zalogowany. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>Plik publishManifest

Plik publishManifest jest używany przez **publikowania** polecenia. Reprezentuje wszystkie metadane dotyczące rozszerzenia, które witryny Marketplace musi znać. W przypadku rozszerzenia są przekazywane z poziomu rozszerzenia VSIX, właściwość "tożsamość" może mieć tylko Ustaw "internalName". Jest to spowodowane pozostałych właściwości "tożsamość" może zostać wygenerowany na podstawie pliku vsixmanifest. Jeśli rozszerzenie jest msi/exe lub rozszerzenia łącza, użytkownik musi podać pól wymaganych we właściwości "tożsamość". Pozostała część manifest zawiera informacje dotyczące witryny Marketplace (na przykład, kategorii, czy pytań i odpowiedzi jest włączona, itp.).

Przykładowy plik publishManifest rozszerzenia VSIX:

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

Przykładowy plik publishManifest MSI/EXE lub łącza:

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

## <a name="asset-files"></a>Pliki elementów zawartości

Pliki zasobów można przekazać do osadzania elementów, takich jak obrazy w pliku readme. Na przykład, jeśli rozszerzenie zawiera dokument języka znaczników Markdown następujące "Przegląd":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Aby można było rozwiązać "images/testlogo.png" w poprzednim przykładzie, użytkownik może zapewnić "assetFiles" w ich publikowanie manifestu, takich jak poniżej:

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

## <a name="publishing-walkthrough"></a>Przewodnik po publikacji

### <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Tworzenie rozszerzenia programu Visual Studio

W tym przypadku użyjemy rozszerzenia pakietu VSPackage domyślnego, ale te same kroki są prawidłowe dla każdego rodzaju rozszerzenia.

1. Tworzenie pakietu VSPackage w języku C# o nazwie "TestPublish", który zawiera polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie pierwszego rozszerzenia: Witaj, świecie](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Pakiet rozszerzenia

1. Zaktualizuj vsixmanifest rozszerzenia przy użyciu poprawnych informacji o nazwę produktu, autora i wersji.

   ![Aktualizacja rozszerzenia vsixmanifest](media/update-extension-vsixmanifest.png)

2. Tworzenie rozszerzenia w **wersji** trybu. Teraz VSIX w folderze \bin\Release postać Twojego rozszerzenia.

3. Możesz kliknąć dwukrotnie VSIX, aby zweryfikować instalację.

### <a name="test-the-extension"></a>Testowanie rozszerzenia

 Przed rozpoczęciem dystrybucji rozszerzenia, kompilowanie i testowanie, aby upewnić się, że jest poprawnie zainstalowane w doświadczalnym wystąpieniu programu Visual Studio.

1. W programie Visual Studio Rozpocznij debugowanie. Aby otworzyć doświadczalne wystąpienie programu Visual Studio.

2. W doświadczalnym wystąpieniu, przejdź do **narzędzia** menu i kliknij przycisk **rozszerzenia i aktualizacje...** . Rozszerzenie TestPublish powinna zostać wyświetlona w środkowym okienku i włączone.

3. Na **narzędzia** menu, upewnij się, zobacz polecenia testowania.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publikowanie rozszerzenia w portalu Marketplace za pomocą wiersza polecenia

1. Upewnij się, czy został wcześniej utworzony wersji rozszerzenia i że jest on aktualny.

2. Upewnij się, że utworzono publishmanifest.json i overview.md plików.

3. Otwórz wiersz polecenia i przejdź do katalogu \VSSDK\VisualStudioIntegration\Tools\Bin\ ${VSInstallDir}.

4. Aby utworzyć nowy wydawcy, użyj następującego polecenia:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Po pomyślnym utworzeniu wydawcy zostanie wyświetlony następujący komunikat wiersza polecenia:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Można zweryfikować wydawcy nowe utworzone, przechodząc do [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Aby opublikować nowe rozszerzenie, użyj następującego polecenia:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Po pomyślnym utworzeniu wydawcy zostanie wyświetlony następujący komunikat wiersza polecenia:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Możesz sprawdzić, nowe rozszerzenie opublikowane, przechodząc do [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Należy zainstalować rozszerzenie z witryny Marketplace programu Visual Studio

Teraz, gdy rozszerzenie zostanie opublikowany, zainstaluj go w programie Visual Studio i przetestować.

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje...** .

2. Kliknij przycisk **Online** a następnie wyszukaj TestPublish.

3. Kliknij przycisk **Pobierz**. Rozszerzenia są planowane do zainstalowania.

4. Aby ukończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuń rozszerzenie

Można usunąć rozszerzenie z witryny Marketplace programu Visual Studio i z tego komputera.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Aby usunąć rozszerzenie z witryny Marketplace za pomocą wiersza polecenia

1. Jeśli chcesz usunąć rozszerzenie, użyj następującego polecenia:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Na pomyślne usunięcie rozszerzenia zostanie wyświetlony następujący komunikat wiersza polecenia:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenie z komputera

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

2. Wybierz pozycję "MyVsixExtension", a następnie kliknij przycisk **Odinstaluj**. Rozszerzenie następnie zostanie zaplanowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
