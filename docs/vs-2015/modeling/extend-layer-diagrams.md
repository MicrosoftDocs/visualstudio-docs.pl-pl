---
title: Rozszerzanie diagramów warstwowych | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302337"
---
# <a name="extend-layer-diagrams"></a>Rozszerzone diagramy warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać kod, aby utworzyć i zaktualizować diagramy warstwowe oraz sprawdzić poprawność struktury kodu programu względem diagramów warstwowych w programie Visual Studio. Można dodawać polecenia wyświetlane w menu skrótów (kontekstowych) diagramów, dostosowywać gesty przeciągania i upuszczania oraz uzyskiwać dostęp do modelu warstwy za pomocą szablonów tekstu. Rozszerzenia te można spakować do rozszerzenia integracji programu Visual Studio (VSIX) i rozpowszechniać je do innych użytkowników programu Visual Studio.

 Aby uzyskać więcej informacji na temat diagramów warstwowych, zobacz:

- [Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)

- [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)

## <a name="requirements"></a><a name="prereqs"></a>Wymagania
 Na komputerze musi być zainstalowane następujące elementy:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [SDK modelowania dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  Na komputerze musi być zainstalowana odpowiednia wersja programu Visual Studio, na której chcesz uruchomić rozszerzenia warstwy. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md).

  Aby zobaczyć, które wersje diagramów warstwowych programu Visual Studio obsługują diagramy warstwowe, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>W tej sekcji
 [Dodawanie poleceń i gestów do diagramów warstw](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Dodawanie niestandardowej walidacji architektury do diagramów warstw](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Dodawanie właściwości niestandardowych do diagramów warstw](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md)

 [Rozwiązywanie problemów z rozszerzeniami dla diagramów warstw](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Zobacz też
 [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md) [Diagramy warstw:](../modeling/layer-diagrams-reference.md) [Diagramy warstw referencyjnych: Wskazówki](../modeling/layer-diagrams-guidelines.md) Tworzenie [diagramów warstwowych na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md) Sprawdzanie poprawności kodu za pomocą [diagramów warstwowych Generowanie](../modeling/validate-code-with-layer-diagrams.md) plików z modelu [UML](../modeling/generate-files-from-a-uml-model.md) Otwórz model [UML przy użyciu interfejsu API programu Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
