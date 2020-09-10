---
title: Wprowadzenie do rozszerzeń usługi językowej i edytora
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94ccda92a0ad5508b8e14ec267f32c50b64e55c0
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742892"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Wprowadzenie do rozszerzeń usługi językowej i edytora

Rozszerzenia edytora umożliwiają dodawanie funkcji usługi językowej, takich jak konspekt, dopasowywanie nawiasów klamrowych, IntelliSense i żarówki do własnego języka programowania lub dowolnego typu zawartości. Możesz również dostosować wygląd i zachowanie edytora programu Visual Studio, na przykład Kolorowanie tekstu, marginesy, elementy definiowania i inne wizualizacje. Możesz również zdefiniować własny typ zawartości i określić wygląd i zachowanie widoków tekstu, w których wyświetlana jest zawartość.

 Aby rozpocząć pisanie rozszerzeń edytora, użyj szablonów projektu edytora zainstalowanych w ramach zestawu Visual Studio SDK. Visual Studio SDK to zestaw narzędzi do pobrania, które ułatwiają tworzenie rozszerzeń programu Visual Studio przy użyciu pakietów VSPackage lub za pomocą Managed Extensibility Framework (MEF).

> [!NOTE]
> Aby uzyskać więcej informacji na temat zestawu Visual Studio SDK, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Zalecamy zapoznanie się z poniższymi pojęciami i technologiami przed napisaniem własnych rozszerzeń edytora.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) i rozszerzenia edytora

 Interfejs użytkownika edytora programu Visual Studio jest implementowany przy użyciu Windows Presentation Foundation (WPF). WPF zawiera bogate środowisko wizualne i spójny model programowania, który oddziela aspekty wizualne kodu od logiki biznesowej. Podczas tworzenia rozszerzeń edytora można używać wielu elementów i funkcji WPF. Aby uzyskać więcej informacji, zobacz [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) i rozszerzenia edytora

 Edytor programu Visual Studio używa Managed Extensibility Framework (MEF) do zarządzania jego składnikami i rozszerzeniami. MEF umożliwia również deweloperom łatwiejsze tworzenie rozszerzeń dla aplikacji hosta, takich jak Visual Studio. W tym środowisku należy zdefiniować rozszerzenie zgodnie z umową MEF i wyeksportować ją jako część składnika MEF. Aplikacja hosta zarządza częściami składników, wyszukując je, rejestrując je i upewniając się, że są one stosowane do prawidłowego kontekstu.

> [!NOTE]
> Aby uzyskać więcej informacji na temat MEF w edytorze, zobacz [Managed Extensibility Framework w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Punkty rozszerzenia i rozszerzenia edytora programu Visual Studio

 Punkty rozszerzenia edytora to części składników MEF, które można dostosowywać i rozszerzać. W niektórych przypadkach rozszerzasz punkt rozszerzenia, implementując interfejs i eksportując go wraz z prawidłowymi metadanymi. W innych przypadkach wystarczy zadeklarować rozszerzenie i wyeksportować je jako określony typ.

 Poniżej przedstawiono niektóre podstawowe rodzaje rozszerzeń edytora:

- Marginesy i paski przewijania

- Tagi

- Zakończeń

- Opcje

- IntelliSense

  Aby uzyskać więcej informacji na temat punktów rozszerzenia edytora, zobacz [punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Wdrażanie rozszerzeń edytora

 W programie Visual Studio wdrażasz rozszerzenia edytora przez dodanie pliku metadanych o nazwie *source. Extension. vsixmanifest* do rozwiązania, skompilowanie rozwiązania, a następnie dodanie kopii plików binarnych i manifestu w folderze, który jest znany w programie Visual Studio. Plik manifestu definiuje podstawowe informacje o rozszerzeniu (na przykład nazwę, autora, wersję i typ zawartości). Aby uzyskać więcej informacji na temat pliku manifestu VSIX i sposobu wdrażania rozszerzeń, zobacz temat [dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Podczas instalowania rozszerzenia na komputerze należy uwzględnić pliki binarne i manifest w podfolderze folderu znanego dla programu Visual Studio.

> [!WARNING]
> Nie trzeba martwić się o szczegóły manifestów i lokalizacji wdrożenia, jeśli używasz jednego z szablonów rozszerzalności edytora, które znajdują się w programie Visual Studio. Szablony zawierają wszystkie elementy wymagane do zarejestrowania i wdrożenia rozszerzenia.

## <a name="run-extensions-in-the-experimental-instance"></a>Uruchamianie rozszerzeń w eksperymentalnym wystąpieniu

 Możesz izolować swoją działającą wersję programu Visual Studio podczas tworzenia rozszerzenia, wdrażając je w następującym folderze eksperymentalnym (w systemach Windows Vista i Windows 7):

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {ExtensionID}*

 gdzie *% LocalAppData%* jest nazwą zalogowanego użytkownika, *firma* jest nazwą firmy, która jest właścicielem rozszerzenia, a *ExtensionID* jest identyfikatorem rozszerzenia.

 Po wdrożeniu rozszerzenia do lokalizacji eksperymentalnej jest ona uruchamiana w trybie debugowania. Drugie wystąpienie programu Visual Studio jest uruchomione i nosi nazwę **Microsoft Visual Studio — wystąpienie eksperymentalne**.

## <a name="manage-extensions"></a>Zarządzanie rozszerzeniami

 Rozszerzenia programu Visual Studio są wymienione w temacie **rozszerzenia i aktualizacje** (w menu **Narzędzia** ). Jeśli testujesz rozszerzenie w eksperymentalnym wystąpieniu, jest ono wyświetlane w obszarze **rozszerzenia i aktualizacje** w wystąpieniu eksperymentalnym, ale nie jest wymienione w wystąpieniu deweloperskim.

 Aby uzyskać więcej informacji, zobacz [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Tworzenie rozszerzeń edytora przy użyciu szablonów

 Za pomocą szablonów edytora można tworzyć rozszerzenia MEF, które dostosowują klasyfikatory, zakończenia i marginesy. Istnieją szablony dla projektów C# i Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Do tworzenia rozszerzeń można także użyć szablonu projektu VSIX. Ten szablon zawiera tylko te elementy, które są wymagane do wdrożenia dowolnego rodzaju rozszerzenia i obejmują plik *source. Extension. vsixmanifest* , wymagane odwołania do zestawu i plik projektu zawierający zadania kompilacji, które umożliwiają wdrożenie rozszerzenia. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

 Można również tworzyć składniki MEF edytora z rozszerzenia pakietu programu Visual Studio. Szczegółowe informacje znajdują się w następujących przewodnikach:

- [Wskazówki: Używanie polecenia powłoki z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Zobacz także

- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
