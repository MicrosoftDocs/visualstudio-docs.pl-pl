---
title: Dokumentowanie Windows | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 490c39b9e97ad6a55ca2d1695d31b85ecc13dc57
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418597"
---
# <a name="document-windows"></a>Okna dokumentów
W programie Visual Studio *okno dokumentu* jest oknem podrzędnym ramce, który jest skojarzony z okna interfejsu wielu dokumentów (MDI). Okna dokumentów są zwykle używane do wyświetlania i modyfikacji kodu źródłowego lub tekstu, ale może to również obsługiwać inne typy funkcjonalności. Okna dokumentów:

- Można organizować w osobnej karcie poziomej lub pionowej grupach w obiekcie nadrzędnym MDI tak, aby wiele plików mogą być wyświetlane w tym samym czasie.

- Może być zadokowane w dowolnej kolejności w elemencie nadrzędnym MDI.

- Mogą być swobodnie przestawione.

- Są połączone w kolejności tabulacji na inne okna MDI.

  Polecenia grupowania zadokowane i przestawne znajdują się w menu skrótów dla karty okna dokumentu.

  Aby uzyskać więcej informacji na temat zachowanie okna w programie Visual Studio, zobacz [dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementacja okna dokumentów
 Okna dokumentów są tworzone przez zaimplementowanie edytora. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Interfejs tworzył okien dokumentu jako część tworzenia wystąpienia edytora. Aby uzyskać więcej informacji, zobacz [interfejsy starszej wersji, w edytorze](../../extensibility/legacy-interfaces-in-the-editor.md).

> [!NOTE]
> Aby zapewnić Wstecz i przekazywać je punktów nawigacji w oknie, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfejsu. Edytor tekstu używa znaczników tekstu, aby zidentyfikować punkty nawigacji w dokumencie.

## <a name="the-running-document-table"></a>Uruchamianie tabeli dokumentów
 IDE używa uruchamianie tabeli dokumentów (Normalizacją) umożliwia śledzenie stanu okna dokumentu. Normalizacją to mechanizm, przez który dokument systemu windows są powiadamiani o zdarzenia, takie jak po zamknięciu rozwiązania lub plik został zmodyfikowany. Aby uzyskać więcej informacji, zobacz [uruchamianie tabeli dokumentu](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Zobacz także
- [Opóźnione ładowanie dokumentu](../../extensibility/internals/delayed-document-loading.md)