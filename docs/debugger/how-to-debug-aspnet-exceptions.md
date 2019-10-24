---
title: 'Instrukcje: debugowanie wyjątków ASP.NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 9f8391d355b2f540db4e38486b8992d940336464
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733788"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Porady: debugowanie wyjątków ASP.NET
Debugowanie wyjątków jest ważną częścią opracowywania niezawodnej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji. Ogólne informacje o sposobie debugowania wyjątków polegają na [zarządzaniu wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md).

 Aby debugować Nieobsłużone wyjątki [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], należy się upewnić, że debuger go zatrzyma. Środowisko uruchomieniowe [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ma program obsługi wyjątków najwyższego poziomu. W związku z tym debuger nigdy nie jest podzielony na Nieobsłużone wyjątki domyślnie. Aby przerwać debuger w przypadku zgłoszenia wyjątku, należy wybrać opcję **Przerwij, gdy wyjątek to: zgłoszone** ustawienie dla tego konkretnego wyjątku w oknie dialogowym **wyjątki** .

 Jeśli włączono Tylko mój kod, Przerwij, **gdy wyjątek to: zgłoszone** nie powoduje, że debuger przerwie się natychmiast, jeśli wystąpi wyjątek w metodzie .NET lub innym kodzie systemowym. Zamiast tego wykonywanie jest kontynuowane do momentu, aż debuger trafi w kodzie niesystemowym, spowoduje przerwanie działania. W związku z tym nie trzeba wykonywać kroków kodu systemowego, gdy wystąpi wyjątek.

 Tylko mój kod daje kolejną opcję, która może być jeszcze bardziej przydatna: **Przerwij, gdy wyjątek jest: nieobsługiwany przez użytkownika**. W przypadku wybrania tego ustawienia dla wyjątku debuger przerwie wykonywanie w kodzie użytkownika, ale tylko wtedy, gdy wyjątek nie zostanie przechwycony i obsłużony przez kod użytkownika. To ustawienie powoduje negację efektu obsługi wyjątków [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] najwyższego poziomu, ponieważ program obsługi znajduje się w kodzie innym niż użytkownik.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Aby włączyć debugowanie wyjątków ASP.NET z Tylko mój kod

1. W menu **debugowanie** kliknij pozycję **wyjątki**.

     Zostanie wyświetlone okno dialogowe **wyjątki** .

2. W wierszu **wyjątki środowiska uruchomieniowego języka wspólnego** wybierz opcję **zgłoszone** lub **nieobsługiwane przez użytkownika**.

     Aby można było użyć ustawienia **nieobsługiwanego przez użytkownika** , należy włączyć **tylko mój kod** ..

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Aby użyć najlepszych rozwiązań dla obsługi wyjątków ASP.NET

- Umieść `try ... catch` bloki wokół kodu, który może generować wyjątki, które można przewidywanie i wiedzieć, jak obsłużyć. Na przykład jeśli aplikacja przeprowadza wywołania do usługi sieci Web XML lub bezpośrednio do SQL Server, ten kod powinien znajdować się w **try... bloki catch** , ponieważ mogą wystąpić liczne wyjątki.

## <a name="see-also"></a>Zobacz także
- [Debuguj aplikacje ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)