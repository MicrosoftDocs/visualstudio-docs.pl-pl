---
title: Porównaj folder projektu z magazynem kontroli źródła | Microsoft Docs
description: W interfejsie API wtyczki kontroli źródła porównanie między lokalnym folderem projektu i kontrolą źródła jest realizowane przy użyciu SccDirQueryInfo i SccDirDiff.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ed69c6e503614cd1b2ed8e21716a5edcb4babd2b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877588"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Opcjonalne porównanie lokalnego folderu projektu do magazynu kontroli kodu źródłowego
W interfejsie API wtyczki kontroli źródła 1,2 porównanie między lokalnym folderem projektu a kontrolą źródła jest realizowane przy użyciu funkcji [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 W **Eksplorator rozwiązań**, jeśli wybrano folder zamiast pojedynczego pliku, menu skrótów do **porównywania wersji** wywoła nowe [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) i [SccDirDiff](../../extensibility/sccdirdiff-function.md) w dodatku plug-in kontroli źródła.

## <a name="new-capability-flags"></a>Nowe flagi możliwości
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Nowe funkcje
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 `SccDirQueryInfo`Funkcja jest wywoływana przed `SccDirDiff` określeniem, czy katalog roboczy jest kontrolowany przez źródło. `SccDirDiff`Funkcja wyświetla różnice między bieżącym katalogiem lokalnym i odpowiednim folderem kontroli źródła. To polecenie monituje wtyczkę kontroli źródła, aby wyświetlić listę zmian w katalogu. Wtyczka do kontroli źródła zapewnia własny interfejs użytkownika do wyświetlania różnic.

> [!NOTE]
> Ta funkcja używa tych samych flag poleceń co [SccDiff](../../extensibility/sccdiff-function.md). Jako dostawca wtyczki kontroli źródła możesz zdecydować, aby nie obsługiwać operacji "szybkiej diff" dla katalogów.

## <a name="see-also"></a>Zobacz też
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
