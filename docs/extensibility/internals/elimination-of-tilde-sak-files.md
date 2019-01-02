---
title: Eliminacja ~ SAK plików | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37d2d8fbbd98e75b398caec9e4c2f36a5853ba4a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53862817"
---
# <a name="elimination-of-sak-files"></a>Eliminacja ~ SAK plików
W 1.2 interfejsu API wtyczki kontroli źródła *~ SAK* pliki zostały zastąpione przez flagi funkcji i nowych funkcji, które wykryć, czy źródło kontrolować obsługuje wtyczki *MSSCCPRJ* plików i współdzielonymi wyewidencjonowaniami.  
  
## <a name="sak-files"></a>~ Plików SAK  
Visual Studio .NET 2003 utworzone pliki tymczasowe z prefiksem *~ SAK*. Te pliki są używane do określenia, czy obsługuje wtyczki kontroli źródła:  
  
- *MSSCCPRJ.SCC* pliku.  
  
- Wiele operacji wyewidencjonowania (współużytkowane).  
    
Wtyczek, które obsługują zaawansowane funkcje udostępniane w 1.2 interfejsu API wtyczki kontroli źródła IDE może wykryć tych funkcji bez tworzenia plików tymczasowych za pomocą nowych możliwości, flag i funkcje, szczegółowo opisane w poniższych sekcjach.  
  
## <a name="new-capability-flags"></a>Nowe flagi możliwości  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nowe funkcje  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Jeśli wtyczka do kontroli źródła, obsługuje wielu wyewidencjonowania (współużytkowane), a następnie deklaruje `SCC_CAP_MULTICHECKOUT` możliwości i implementuje `SccIsMultiCheckOutEnabled` funkcji. Ta funkcja jest wywoływana zawsze wtedy, gdy operacja wyewidencjonowania odbywa się na żaden z projektów pod kontrolą źródła.  
  
 Jeśli wtyczka do kontroli źródła obsługuje stworzeniem i używaniem *MSSCCPRJ.SCC* pliku, a następnie deklaruje `SCC_CAP_SCCFILE` możliwości i implementuje [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Ta funkcja jest wywoływana z listą plików. Funkcja zwraca `TRUE' or 'FALSE` dla każdego pliku wskazać, czy należy używać programu Visual Studio *MSSCCPRJ.SCC* go w pliku. Jeśli wtyczka do kontroli źródła nie zdecyduje się na obsługuje te nowe możliwości i funkcje, on używać następujący klucz rejestru, aby wyłączyć tworzenie tych plików:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateTemporaryFilesInSourceControl** = *DWORD: 00000001*  
  
> [!NOTE]
>  Jeśli ten klucz rejestru jest ustawiony na *DWORD: 00000000*odpowiada kluczowi trwa nieistniejącej i programu Visual Studio nadal podejmuje próbę utworzenia plików tymczasowych. Jednakże jeśli klucz rejestru jest ustawiony na *DWORD: 00000001*, Visual Studio nie jest podejmowana próba tworzenia tymczasowych plików. Zamiast tego przyjęto założenie, że wtyczka do kontroli źródła nie obsługuje *MSSCCPRJ.SCC* pliku, a nie obsługuje współdzielonymi wyewidencjonowaniami.  
  
## <a name="see-also"></a>Zobacz także  
 [What's new in źródła kontrolki wtyczki API wersji 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)