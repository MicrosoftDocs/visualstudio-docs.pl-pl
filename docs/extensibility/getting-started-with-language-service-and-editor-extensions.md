---
title: Wprowadzenie do usługi językowej i edytora rozszerzenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bd39ab8abde2fdbe337073e7cfaa7ea457b022f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342448"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Wprowadzenie do usługi i Edytor rozszerzenia językowe
Rozszerzenia edytora służy do dodawania funkcji języka, np. Tworzenie konspektu, parowanie nawiasów klamrowych, funkcja IntelliSense i żarówki, język programowania lub dowolnego typu zawartości. Można również dostosować wygląd i zachowanie edytora programu Visual Studio, na przykład tekst kolorowanie, marginesy, zakończeń i inne elementy wizualne. Można również zdefiniować własny typ zawartości i określ wygląd i zachowanie widoki tekstowe, w których zawartość zostanie wyświetlona.

 Aby rozpocząć pisanie rozszerzenia edytora, korzystanie z szablonów projektów edytora, które są zainstalowane jako część programu Visual Studio SDK. Visual Studio SDK jest dostępny do pobrania zestaw narzędzi, które ułatwiają tworzenie rozszerzeń programu Visual Studio przy użyciu pakietów VSPackage lub za pomocą Managed Extensibility Framework (MEF).

> [!NOTE]
> Aby uzyskać więcej informacji na temat zestawu SDK programu Visual Studio, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Firma Microsoft zaleca, Dowiedz się o następujących pojęć i technologii przed przystąpieniem do napisania własnego rozszerzenia edytora.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Rozszerzenia Windows Presentation Foundation (WPF) i edytora
 Interfejs użytkownika edytora programu Visual Studio (UI) jest implementowany przy użyciu Windows Presentation Foundation (WPF). WPF zapewnia bogate doświadczenia wizualne i spójny model programowania, która oddziela visual aspektów kod od logiki biznesowej. Po utworzeniu rozszerzenia edytora, można użyć wielu elementów WPF i funkcje. Aby uzyskać więcej informacji, zobacz [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Rozszerzenia Managed Extensibility Framework (MEF) i edytora
 Edytor programu Visual Studio używa Managed Extensibility Framework (MEF) do zarządzania komponentami i rozszerzeń. MEF umożliwia również deweloperom więcej łatwe tworzenie rozszerzeń dla aplikacji hosta, takimi jak Visual Studio. Ta struktura służy do definiowania rozszerzenia zgodnie z kontrakt MEF i wyeksportuj go jako składnik MEF. Aplikacja hosta zarządza części składowe, ich znajdowanie, rejestrowania ich i upewniając się, że są one stosowane do poprawnego kontekstu.

> [!NOTE]
> Aby uzyskać więcej informacji na temat MEF w edytorze, zobacz [Managed Extensibility Framework, w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Punkty rozszerzenia edytora programu Visual Studio i rozszerzenia
 Punkty rozszerzenia edytora są składniki MEF, które można dostosować i rozszerzyć. W niektórych przypadkach można rozszerzyć punktu rozszerzenia przez implementację interfejs i wyeksportować go wraz z prawidłowych metadanych. W innych przypadkach można po prostu zadeklarować rozszerzenie i wyeksportuj go jako określonego typu.

 Poniżej przedstawiono niektóre z podstawowych rodzajów rozszerzenia edytora:

- Marginesy i paski przewijania

- Znaczniki

- Zakończeń

- Opcje

- IntelliSense

  Aby uzyskać więcej informacji na temat punktów rozszerzenia edytora, zobacz [punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Wdrażanie rozszerzenia Edytora
 W programie Visual Studio, wdrażanie rozszerzenia edytora, dodając plik metadanych o nazwie *source.extension.vsixmanifest* do rozwiązania, należy skompilować rozwiązanie, a następnie dodając kopię plików binarnych i manifest w folderze, który jest znany w programie Visual Studio. Plik manifestu definiuje podstawowych informacji o rozszerzeniu (na przykład nazwy, autora, wersji i typu zawartości). Aby uzyskać więcej informacji na temat pliku manifestu VSIX i sposobu wdrażania rozszerzeń, zobacz [rozszerzeń programu Visual Studio statku](../extensibility/shipping-visual-studio-extensions.md).

 Po zainstalowaniu rozszerzenia na komputerze obejmują pliki binarne i manifest w podfolderze folderu, który jest znany dla programu Visual Studio.

> [!WARNING]
> Nie trzeba martwić o szczegóły manifesty i lokalizacji wdrożenia, jeśli używasz jednego z szablonów rozszerzania edytora, które znajdują się w programie Visual Studio. Szablony zawierają wszystko, co jest wymagane, aby zarejestrować i wdrożyć rozszerzenie.

## <a name="run-extensions-in-the-experimental-instance"></a>Uruchamianie rozszerzenia w doświadczalnym wystąpieniu
 Można związane z działającą wersją programu Visual Studio, gdy rozszerzenie jest tworzona przez wdrożenie jej w następującym folderze eksperymentalne (w systemach Windows Vista i Windows 7):

 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions\\{Company}\\{ExtensionID}*

 gdzie *% LOCALAPPDATA %* jest nazwą użytkownika zalogowanego *firmy* to nazwa firmy, który jest właścicielem rozszerzenia, a *ExtensionID* jest Identyfikatorem rozszerzenia.

 Podczas wdrażania rozszerzenia w doświadczalnych lokalizacji działa w trybie debugowania. Drugie wystąpienie programu Visual Studio jest uruchomiony i nosi nazwę **Microsoft Visual Studio — wystąpienie doświadczalne**.

## <a name="manage-extensions"></a>Zarządzaj rozszerzeniami
 Rozszerzenia programu Visual Studio są wymienione w **rozszerzenia i aktualizacje** (na **narzędzia** menu). Jeśli testujesz rozszerzenia w doświadczalnym wystąpieniu, jest ono wyświetlane w **rozszerzenia i aktualizacje** w doświadczalnym wystąpieniu, ale nie znajduje się w wystąpieniu rozwoju.

 Aby uzyskać więcej informacji, zobacz [wyszukiwanie i korzystanie z rozszerzenia programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Użyj szablonów do tworzenia rozszerzenia Edytora
 Szablony edytora umożliwia tworzenie rozszerzeń MEF, umożliwiające dostosowanie klasyfikatorów, zakończeń oraz marginesy. Brak szablonów dla projektów w językach C# i Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Szablon projektu VSIX umożliwia również tworzenie rozszerzeń. Ten szablon zawiera tylko elementy, które są wymagane do wdrażania wszelkiego rodzaju rozszerzenia i obejmują *source.extension.vsixmanifest* pliku, wymagane odwołania do zestawu i pliku projektu, który obejmuje zadania kompilacji Pozwala wdrożyć rozszerzenie. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).

 Można również utworzyć edytora składników MEF z rozszerzeniem pakiet rozszerzeń Visual Studio. Zobacz poniższe poradniki, aby uzyskać szczegółowe informacje:

- [Przewodnik: Używanie polecenia programu PowerShell z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Przewodnik: Używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Zobacz także
- [Punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)