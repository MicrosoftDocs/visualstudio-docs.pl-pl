---
title: Porównaj folder projektu z magazynem kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706862"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Opcjonalne porównanie lokalnego folderu projektu do magazynu kontroli kodu źródłowego
W usłudze Source control Plug-in API 1.2 porównanie lokalnego folderu projektu i kontroli źródła odbywa się za pomocą funkcji [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 W **Eksploratorze rozwiązań,** jeśli folder jest zaznaczony zamiast pojedynczego pliku, menu **skrótów Porównaj wersje** wywołuje nowe [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [SccDirDiff](../../extensibility/sccdirdiff-function.md) w uszczelce formantu źródłowego.

## <a name="new-capability-flags"></a>Nowe flagi możliwości
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Nowe funkcje
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Funkcja `SccDirQueryInfo` jest wywoływana wcześniej, `SccDirDiff` aby ustalić, czy katalog roboczy jest kontrolowany przez źródło. Funkcja `SccDirDiff` wyświetla różnice między bieżącym katalogiem lokalnym a odpowiednim folderem kontroli źródła. To polecenie prosi wtyczkę formantu źródła o wyświetlenie listy zmian w katalogu. Wtyczka kontroli źródła udostępnia własny interfejs użytkownika, aby wyświetlić różnice.

> [!NOTE]
> Ta funkcja używa tych samych flag poleceń co [SccDiff](../../extensibility/sccdiff-function.md). Jako dostawca wtyczki kontroli źródła możesz nie obsługiwać operacji "szybki diff" dla katalogów.

## <a name="see-also"></a>Zobacz też
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
