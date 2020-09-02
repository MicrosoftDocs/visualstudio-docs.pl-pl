---
title: Proces hostingu (vshost.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a998246f514f13a575f6a7fef850f9f705f92553
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645530"
---
# <a name="hosting-process-vshostexe"></a>Proces hostingu (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces hostingu to funkcja w programie Visual Studio, która zwiększa wydajność debugowania, umożliwia debugowanie częściowej relacji zaufania i umożliwia Obliczanie wyrażenia czasu projektowania. Pliki procesu hostingu zawierają vshost w nazwie pliku i są umieszczane w folderze wyjściowym projektu. Aby uzyskać więcej informacji, zobacz [debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md).

> [!NOTE]
> Pliki procesów hostingu (.vshost.exe) są używane przez program Visual Studio i nie powinny być uruchamiane bezpośrednio ani wdrażane za pomocą aplikacji.

## <a name="improved-debugging-performance"></a>Ulepszona wydajność debugowania
 Proces hostingu tworzy domenę aplikacji i kojarzy debugera z aplikacją. Wykonanie tych zadań może spowodować zauważalne opóźnienie między rozpoczęciem debugowania a czasem rozpoczęcia działania aplikacji. Proces hostingu pozwala zwiększyć wydajność przez utworzenie domeny aplikacji i skojarzenie debugera w tle oraz zapisanie domeny aplikacji i stanu debugera między uruchomieniami aplikacji. Aby uzyskać więcej informacji na temat domen aplikacji, zobacz [domeny aplikacji](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).

## <a name="partial-trust-debugging"></a>Debugowanie częściowej relacji zaufania
 Aplikacja może być określona jako aplikacja częściowej relacji zaufania na [stronie zabezpieczenia](../ide/reference/security-page-project-designer.md) **projektanta projektu**. Debugowanie częściowej aplikacji zaufania wymaga specjalnego zainicjowania domeny aplikacji. Ta Inicjalizacja jest obsługiwana przez proces hostingu.

## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażeń czasu projektowania
 Obliczanie wyrażeń w czasie projektowania umożliwia testowanie kodu z okna **bezpośredniego** bez konieczności uruchamiania aplikacji. Proces hostingu wykonuje ten kod podczas obliczania wyrażenia czasu projektowania. Aby uzyskać więcej informacji, zobacz [okno bezpośrednie](../ide/reference/immediate-window.md).

## <a name="see-also"></a>Zobacz też
 [Debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md) [— instrukcje: wyłączanie](../ide/how-to-disable-the-hosting-process.md) [bezpośrednich](../ide/reference/immediate-window.md) [domen aplikacji](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8) okna procesu hostingu
