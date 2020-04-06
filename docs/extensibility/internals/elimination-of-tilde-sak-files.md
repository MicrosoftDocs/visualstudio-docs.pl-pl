---
title: Eliminacja plików ~SAK | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708502"
---
# <a name="elimination-of-sak-files"></a>Eliminacja plików ~SAK
W interfejsie API 1.2 wtyczki source control 1.2 pliki *~SAK* zostały zastąpione flagami możliwości i nowymi funkcjami, które wykrywają, czy wtyczka kontroli źródła obsługuje plik *MSSCCPRJ* i udostępnione wyewidencjonowania.

## <a name="sak-files"></a>Pliki ~SAK
Program Visual Studio .NET 2003 utworzył pliki tymczasowe poprzedzone *programem ~SAK*. Pliki te służą do określenia, czy obsługuje wtyczkę kontroli źródła:

- Plik *MSSCCPRJ.SCC.*

- Wiele (udostępnionych) transakcji.

W przypadku wtyczek obsługujących zaawansowane funkcje dostępne w interfejsie API 1.2 wtyczki kontroli źródła IDE może wykryć te możliwości bez tworzenia plików tymczasowych za pomocą nowych możliwości, flag i funkcji, wyszczególnionych w poniższych sekcjach.

## <a name="new-capability-flags"></a>Nowe flagi możliwości
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nowe funkcje
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Jeśli wtyczka kontroli źródła obsługuje wiele (udostępnionych) wyewidencjonowania, deklaruje `SCC_CAP_MULTICHECKOUT` tę funkcję i implementuje `SccIsMultiCheckOutEnabled` tę funkcję. Ta funkcja jest wywoływana za każdym razem, gdy operacja wyewidencjonowania występuje w dowolnym z projektów kontrolowanych przez źródło.

 Jeśli wtyczka kontroli źródła obsługuje tworzenie i używanie pliku *MSSCCPRJ.SCC,* `SCC_CAP_SCCFILE` deklaruje tę funkcję i implementuje [plik SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Ta funkcja jest wywoływana z listą plików. Funkcja zwraca `TRUE' or 'FALSE` dla każdego pliku, aby wskazać, czy visual studio należy użyć pliku *MSSCCPRJ.SCC* dla niego. Jeśli wtyczka kontroli źródła nie obsługuje tych nowych funkcji i funkcji, może użyć następującego klucza rejestru, aby wyłączyć tworzenie tych plików:

 **[HKEY_CURRENT_USER\Oprogramowanie\Microsoft\VisualStudio\8.0\Kontrola źródła] DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Jeśli ten klucz rejestru jest ustawiony na *dword:00000000*, jest odpowiednikiem klucza, który nie istnieje, a program Visual Studio nadal próbuje utworzyć pliki tymczasowe. Jeśli jednak klucz rejestru jest ustawiony na *dword:00000001,* program Visual Studio nie próbuje utworzyć plików tymczasowych. Zamiast tego zakłada, że wtyczka kontroli źródła nie obsługuje pliku *MSSCCPRJ.SCC* i nie obsługuje wyewidencjonowania udostępnionego.

## <a name="see-also"></a>Zobacz też
- [Co nowego w interfejsie API wtyczki kontroli źródła w wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
