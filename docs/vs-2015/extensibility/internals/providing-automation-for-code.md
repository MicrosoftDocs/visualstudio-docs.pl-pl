---
title: Zapewnianie automatyzacji kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 399900bce10edbd6fec549fc3a52ca3dbeefdabc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761561"
---
# <a name="providing-automation-for-code"></a>Zapewnianie automatyzacji kodu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tworzenie modelu automatyzacji dla kodu nie jest wymagana. Zestaw SDK środowiska nie zapewnia próbkę aby to zrobić. Szczegółowe informacje na temat modele kodu, zobacz <xref:EnvDTE.CodeModel> obiektu.  
  
 Aby zaimplementować modelu kodu, należy zaimplementować żadnych interfejsów, które są określane przez strukturę danych wewnętrznych. Obiekty musi pochodzić od `IDispatch` klasy.  
  
 Obiekty, które można rozszerzyć <xref:EnvDTE.CodeModel> i <xref:EnvDTE.FileCodeModel>, są dostępne z <xref:EnvDTE.Project> obiektu i wyglądać podobnie do następującego:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Możesz wybrać opcję wdrożenia po prostu z `CodeModel` lub `FileCodeModel` interfejsu w obiekcie zwracanie z Twojej `Project` i <xref:EnvDTE.ProjectItem> obiektów. Można korzystać z funkcji w tym interfejsie, który jest odpowiedni dla używanego systemu projektu.  
  
 Jeśli chcesz dodać funkcje, takie jak metody lub właściwości, które nie są dostępne ze standardu `CodeModel` i `FileCodeModel` interfejsów, utworzyć własny interfejs, który dziedziczy standard. Pamiętaj dokumentów za pomocą systemu projektu, aby użytkownicy końcowi będą wiedzieli, do wyszukania go. Zwraca standardowy interfejs, ale użytkownik może wywołać `QueryInterface` metody lub Rzutowanie do interfejsu, jeśli jest on znany istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)

