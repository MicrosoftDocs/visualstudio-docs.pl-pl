---
title: Wprowadzenie do usługi językowej i rozszerzeń edytora | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711308"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Wprowadzenie do usług językowych i rozszerzeń edytora
Rozszerzenia edytora można używać do dodawania funkcji usługi języka, takich jak tworzenie nakreślenia, dopasowywanie nawiasów klamrowych, IntelliSense i żarówki do własnego języka programowania lub do dowolnego typu zawartości. Można również dostosować wygląd i zachowanie edytora Visual Studio, na przykład kolorowanie tekstu, marginesy, ozdoby i inne elementy wizualne. Można również zdefiniować własny typ zawartości i określić wygląd i zachowanie widoków tekstu, w których jest wyświetlana zawartość.

 Aby rozpocząć pisanie rozszerzeń edytora, należy użyć szablonów projektu edytora, które są zainstalowane jako część visual studio SDK. Visual Studio SDK jest zestawem narzędzi do pobrania, które ułatwiają tworzenie rozszerzeń programu Visual Studio, za pomocą VSPackages lub przy użyciu managed extensibility framework (MEF).

> [!NOTE]
> Aby uzyskać więcej informacji na temat sdk programu Visual Studio, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Przed napisaniem własnych rozszerzeń edytora należy zapoznać się z następującymi pojęciami i technologiami.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) i rozszerzenia edytora
 Interfejs użytkownika edytora Visual Studio (UI) jest implementowany przy użyciu programu Windows Presentation Foundation (WPF). WPF WPF zapewnia bogate środowisko wizualne i spójny model programowania, który oddziela wizualne aspekty kodu od logiki biznesowej. Podczas tworzenia rozszerzeń edytora można używać wielu elementów i funkcji WPF. Aby uzyskać więcej informacji, zobacz [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Zarządzane ramy rozszerzalności (MEF) i rozszerzenia edytora
 Edytor programu Visual Studio używa managed extensibility framework (MEF) do zarządzania jego składników i rozszerzeń. MEF umożliwia również deweloperom łatwiej tworzyć rozszerzenia dla aplikacji hosta, takich jak Visual Studio. W tej ramach można zdefiniować rozszerzenie zgodnie z umową MEF i wyeksportować go jako część składnika MEF. Aplikacja hosta zarządza częściami składowymi, znajdując je, rejestrując je i upewniając się, że są one stosowane do prawidłowego kontekstu.

> [!NOTE]
> Aby uzyskać więcej informacji na temat MEF w edytorze, zobacz [Managed Extensibility Framework w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Punkty rozszerzeń edytora i rozszerzenia edytora programu Visual Studio
 Punkty rozszerzenia edytora to części składowe MEF, które można dostosować i rozszerzyć. W niektórych przypadkach można rozszerzyć punkt rozszerzenia, implementując interfejs i eksportując go wraz z poprawnymi metadanymi. W innych przypadkach wystarczy zadeklarować rozszerzenie i wyeksportować go jako określonego typu.

 Oto niektóre z podstawowych rodzajów rozszerzeń edytora:

- Marginesy i paski przewijania

- Tagi

- Ozdoby

- Opcje

- IntelliSense

  Aby uzyskać więcej informacji na temat punktów rozszerzeń [edytora, zobacz Usługi językowe i punkty rozszerzeń edytora](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Wdrażanie rozszerzeń edytora
 W programie Visual Studio można wdrożyć rozszerzenia edytora, dodając plik metadanych o nazwie *source.extension.vsixmanifest* do rozwiązania, tworząc rozwiązanie, a następnie dodając kopię plików binarnych i manifestu w folderze, który jest znany programowi Visual Studio. Plik manifestu definiuje podstawowe fakty dotyczące rozszerzenia (na przykład nazwę, autora, wersję i typ zawartości). Aby uzyskać więcej informacji na temat pliku manifestu VSIX i sposobu wdrażania rozszerzeń, zobacz [Wysyłanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Podczas instalowania rozszerzenia na komputerze, należy uwzględnić pliki binarne i manifest w podfolderze folderu, który jest znany visual studio.

> [!WARNING]
> Nie musisz się martwić o szczegóły manifestów i lokalizacji wdrażania, jeśli używasz jednego z szablonów rozszerzalności edytora, które są zawarte w programie Visual Studio. Szablony zawierają wszystko, co jest wymagane do zarejestrowania i wdrożenia rozszerzenia.

## <a name="run-extensions-in-the-experimental-instance"></a>Uruchamianie rozszerzeń w wystąpieniu eksperymentalnym
 Podczas opracowywania rozszerzenia można ocieplić działającą wersję programu Visual Studio, wdrażając je w następującym folderze eksperymentalnym (w systemach Windows Vista i Windows 7):

 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Rozszerzenia\\{Firma}\\{ExtensionID}*

 gdzie *%LOCALAPPDATA%* jest nazwą zalogowanego użytkownika, *Firma* jest nazwą firmy, która jest właścicielem rozszerzenia, a *ExtensionID* jest identyfikatorem rozszerzenia.

 Po wdrożeniu rozszerzenia do lokalizacji eksperymentalnej, działa w trybie debugowania. Drugie wystąpienie programu Visual Studio jest uruchamiane i nosi nazwę **Microsoft Visual Studio — wystąpienie eksperymentalne**.

## <a name="manage-extensions"></a>Zarządzanie rozszerzeniami
 Rozszerzenia programu Visual Studio są wymienione w **rozszerzenia i aktualizacje** (w menu **Narzędzia).** Jeśli testujesz rozszerzenie w wystąpieniu eksperymentalnym, jest ono wymienione w **rozszerzenia i aktualizacje** w wystąpieniu eksperymentalnym, ale nie jest wymienione w wystąpieniu programistycznego.

 Aby uzyskać więcej informacji, zobacz [Znajdowanie i używanie rozszerzeń programu Visual Studio.](../ide/finding-and-using-visual-studio-extensions.md)

## <a name="use-templates-to-create-editor-extensions"></a>Tworzenie rozszerzeń edytora za pomocą szablonów
 Za pomocą szablonów edytora można tworzyć rozszerzenia MEF, które dostosowują klasyfikatory, ozdoby i marginesy. Istnieją szablony dla projektów języka C# i Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Można również użyć szablonu projektu VSIX do tworzenia rozszerzeń. Ten szablon zawiera tylko elementy, które są wymagane do wdrożenia dowolnego rodzaju rozszerzenia i obejmują plik *source.extension.vsixmanifest,* wymagane odwołania do zestawu i plik projektu, który zawiera zadania kompilacji, które umożliwiają wdrożenie rozszerzenia. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

 Można również utworzyć składniki edytora MEF z rozszerzenia pakietu programu Visual Studio. Szczegółowe informacje można znaleźć w następujących instruktażach:

- [Instruktaż: Używanie polecenia powłoki z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Przewodnik: Używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
