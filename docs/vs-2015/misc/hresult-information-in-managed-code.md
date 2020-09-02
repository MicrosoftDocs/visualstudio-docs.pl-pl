---
title: Informacje o HRESULT w kodzie zarządzanym | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: jillfra
ms.openlocfilehash: 4f80b575656c2d8b1740f217f2e144f89f254078
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681630"
---
# <a name="hresult-information-in-managed-code"></a>Informacje o HRESULT w kodzie zarządzanym
Interakcja między kodem zarządzanym i modelem COM może spowodować problemy w przypadku napotkania wartości zwracanych przez wynik HRESULT.  
  
 W interfejsie COM wartość zwracana HRESULT może odgrywać te role:  
  
- Dostarcz informacje o błędzie (na przykład <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> ).  
  
- Dostarcz informacje o stanie dotyczące normalnego zachowania programu.  
  
  Gdy obiekt COM wywołuje kod zarządzany, HRESULT mogą spowodować następujące problemy:  
  
- Funkcje COM, które zwracają wartości HRESULT mniejsze niż zero (kody błędów) generują wyjątki.  
  
- Metody COM, które regularnie zwracają dwa lub więcej różnych kodów sukcesu, na przykład <xref:Microsoft.VisualStudio.VSConstants.S_OK> lub <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> , nie można wyróżnić.  
  
  Ponieważ wiele [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] funkcji modelu COM zwraca wartości HRESULT mniejsze od zera lub zwracają różne kody sukcesu, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] zestawy międzyoperacyjności zostały zapisaną, aby podpisy metod zostały zachowane. Wszystkie [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] metody międzyoperacyjności są `int` typu. Wartości HRESULT są przesyłane przez warstwę międzyoperacyjną bez zmiany i bez generowania wyjątków.  
  
  Ponieważ funkcja modelu COM zwraca wynik HRESULT do zarządzanej metody, która wywołuje ją, Metoda wywołująca musi sprawdzić wynik HRESULT i zgłosić je w razie potrzeby.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Obsługa HRESULT zwróconych do kodu zarządzanego z modelu COM  
 Gdy wywoływany jest interfejs COM z kodu zarządzanego, należy przeanalizować wartość HRESULT i zgłosić wyjątek, jeśli jest to wymagane. <xref:Microsoft.VisualStudio.ErrorHandler>Klasa zawiera <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metodę, która ZGŁASZA wyjątek com, w zależności od wartości przenoszonego do niego wyniku.  
  
 Domyślnie <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> zgłasza wyjątek, gdy jest przenoszona wynik HRESULT o wartości mniejszej od zera. W przypadkach, gdy takie HRESULT są akceptowalnymi wartościami i żaden wyjątek nie powinien być zgłaszany, wartości dodatkowych HRESULT powinny być przesyłane do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po przetestowaniu wartości. Jeśli wartość HRESULT jest testowana dopasowuje wszystkie wartości HRESULT jawnie przekazaną do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> , żaden wyjątek nie jest zgłaszany.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants>Klasa zawiera stałe dla wspólnych wartości HRESULT, na przykład i <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> , i [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> i <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> udostępnia również <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> metody i <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> , które odpowiadają MAKROm zakończonym powodzeniem i niepowodzeniem w modelu com.  
  
 Rozważmy na przykład następujące wywołanie funkcji, w którym <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> jest akceptowalną wartością zwracaną, ale wszystkie inne HRESULT, które są mniejsze od zera, reprezentują błąd.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Jeśli istnieje więcej niż jedna akceptowalna wartość zwracana, dodatkowe wartości HRESULT mogą wystarczy dołączyć do listy w wywołaniu <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> .  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Zwracanie wartości HRESULT do modelu COM z kodu zarządzanego  
 Jeśli żaden wyjątek nie wystąpi, kod zarządzany zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> do funkcji com, która go wywołała. Międzyoperacyjność modelu COM obsługuje typowe wyjątki, które są jednoznacznie wpisane w kodzie zarządzanym. Na przykład metoda, która odbiera nieakceptowalny `null` argument zgłasza <xref:System.ArgumentNullException> .  
  
 Jeśli nie masz pewności, który wyjątek zgłosić, ale znasz wartość HRESULT, która ma zostać zwrócona do modelu COM, możesz użyć <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metody, aby zgłosić odpowiedni wyjątek. Działa to nawet z niestandardowym błędem, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> próbuje zmapować przekazaną do niego wynik HRESULT na wyjątek silnie określony. Jeśli nie jest to możliwe, zgłasza zamiast niego ogólny wyjątek modelu COM. Ostatecznym wynikiem jest zwrócenie wartości HRESULT <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> z kodu zarządzanego do funkcji com, która wywołała ją.  
  
> [!NOTE]
> Wyjątki naruszają wydajność i mają na celu wskazywanie nietypowych warunków programu. Warunki, które często występują, powinny być obsługiwane wewnętrznie, zamiast zgłoszonego wyjątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzane pakietów VSPackage](../misc/managed-vspackages.md)   
 [Współdziałanie z kodem niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Instrukcje: mapowanie HRESULT i wyjątków](https://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Tworzenie składników COM do międzyoperacyjności](https://msdn.microsoft.com/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Zarządzane pakietów VSPackage](../misc/managed-vspackages.md)