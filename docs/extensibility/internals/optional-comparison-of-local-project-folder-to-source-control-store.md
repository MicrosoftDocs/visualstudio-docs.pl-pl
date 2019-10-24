---
title: Porównaj folder projektu z magazynem kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45bd5b105a2fd24078bc85d8cf5b044351cd78be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726125"
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

 Funkcja `SccDirQueryInfo` jest wywoływana przed `SccDirDiff`, aby określić, czy katalog roboczy jest kontrolowany przez źródło. Funkcja `SccDirDiff` wyświetla różnice między bieżącym katalogiem lokalnym i odpowiednim folderem kontroli źródła. To polecenie monituje wtyczkę kontroli źródła, aby wyświetlić listę zmian w katalogu. Wtyczka do kontroli źródła zapewnia własny interfejs użytkownika do wyświetlania różnic.

> [!NOTE]
> Ta funkcja używa tych samych flag poleceń co [SccDiff](../../extensibility/sccdiff-function.md). Jako dostawca wtyczki kontroli źródła możesz zdecydować, aby nie obsługiwać operacji "szybkiej diff" dla katalogów.

## <a name="see-also"></a>Zobacz także
- [Nowości dotyczące wtyczki kontroli kodu źródłowego w interfejsie API w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)