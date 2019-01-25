---
title: Informacje o HRESULT w kodzie zarządzanym | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2cbb93c5ecb3caf38b686a958d6daed845bdaec7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792794"
---
# <a name="hresult-information-in-managed-code"></a>Informacje o HRESULT w kodzie zarządzanym
Interakcja między kodem zarządzanym i COM może powodować problemy, gdy wystąpią zwracane wartości HRESULT.  
  
 Za pomocą interfejsu COM zwracanej wartości HRESULT można odtworzyć te role:  
  
- Dostarczanie informacji o błędach (na przykład <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>).  
  
- Dostarczaj informacje dotyczące zachowania programu normalnego stanu.  
  
  Wartości HRESULT COM wywołuje kod zarządzany, może spowodować następujące problemy:  
  
- Funkcje modelu COM, które zwracają wartości HRESULT mniejsza od zera (kody błędów) generować wyjątki.  
  
- COM metod zwracających regularnie co najmniej dwóch kodów różnych Powodzenie, na przykład <xref:Microsoft.VisualStudio.VSConstants.S_OK> lub <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, nie może być wyodrębnione.  
  
  Ponieważ wiele [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] funkcje modelu COM, albo zwraca wartość HRESULT mniejszej niż zero lub zwrócić kody sukcesu różnych [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] zapisanych zestawy międzyoperacyjne, tak aby podpisy metod są zachowywane. Wszystkie [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] międzyoperacyjny metody są `int` typu. Wartości HRESULT są przekazywane za pośrednictwem warstwa międzyoperacyjności bez zmian i bez generowania wyjątków.  
  
  Ponieważ funkcja COM zwraca wartość HRESULT do metody zarządzanego, który ją wywołuje, wywoływania metody należy sprawdzić HRESULT i zgłaszają wyjątki, zgodnie z potrzebami.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Obsługa wartości HRESULT zwracane do kodu zarządzanego z modelu COM  
 Po wywołaniu interfejsu COM z kodu zarządzanego, sprawdź wartość HRESULT, aby zgłosić wyjątek, jeśli jest to wymagane. <xref:Microsoft.VisualStudio.ErrorHandler> Klasa zawiera <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> przekazany metody, która zgłasza wyjątek modelu COM., w zależności od wartości HRESULT.  
  
 Domyślnie <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> zgłasza wyjątek, gdy jest przekazywana wartość HRESULT, która ma wartość niższą niż zero. W przypadkach, takich wartości HRESULT są dopuszczalne wartości i nie należy zgłosić wyjątek, wartości dodatkowe wartości HRESULT powinien zostać przekazany do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po wartości są badane. Jeśli HRESULT testowana pasuje do dowolnej wartości HRESULT jawnie przekazany do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, jest zgłaszany żaden wyjątek.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Klasa zawiera stałe dla typowych wartości HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.S_OK> i <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, i [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wartości HRESULT, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> i <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> udostępnia również <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> i <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metod, które odnoszą się do makra Powodzenie, a nie powiodło się w modelu COM.  
  
 Na przykład, należy wziąć pod uwagę poniższe wywołanie funkcji, w którym <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> jest mniejsza niż zero reprezentuje błąd akceptowalną wartość zwracana, ale inne HRESULT.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Jeśli istnieje więcej niż jeden dopuszczalne wartości zwracane, dodatkowe wartości HRESULT tylko można dołączyć do listy w wywołaniu <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Zwracanie wartości HRESULT dla modelu COM z kodu zarządzanego  
 Jeśli nie wystąpi wyjątek, zarządzany kod zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> do funkcji COM, która nazwała go. Usługa międzyoperacyjna modelu COM obsługuje powszechne wyjątki, które są silnie typizowane w kodzie zarządzanym. Na przykład, metody, która odbiera niedopuszczalne `null` zgłasza argument <xref:System.ArgumentNullException>.  
  
 Jeśli nie jesteś niektórych który wyjątków zgłaszają, ale wiesz HRESULT chcesz wrócić do modelu COM, można użyć <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodę, aby zgłosić wyjątek odpowiednie. Dzieje się tak nawet w przypadku błędów niestandardowych, na przykład <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> próbuje zamapować HRESULT przekazany do silnie typizowanego wyjątku. Jeśli jest ona nieosiągalna, zgłosi wyjątek ogólny COM zamiast tego. Ostateczny wynik jest HRESULT, były przekazywane do <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> z kodu zarządzanego jest zwracany do funkcji COM, która nazwała go.  
  
> [!NOTE]
>  Wyjątki wpłynąć na wydajność i są przeznaczone do wskazania niewłaściwym warunków. Warunki, które często występują powinny być obsługiwane w tekście, a nie zgłoszony wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Managed VSPackages](../misc/managed-vspackages.md)   
 [Współdziałanie z kodem niezarządzanym](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Instrukcje: Mapa wyników HRESULT i wyjątków](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Tworzenie składników COM do celów międzyoperacyjności](http://msdn.microsoft.com/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Managed VSPackages](../misc/managed-vspackages.md)