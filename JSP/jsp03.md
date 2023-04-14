EL (Expression Language)
- page, request, session, application의
   attribute, parameter 속성을 사용
- 관련 기본 객체 : pageScope ,
                           requestScope ,
                           sessionScope ,
                           applicationScope ,
                           pageContext , param ,
                           paramValues , cookie ,
                           header , headerValues ,
                           initParam
- 관련 접근자 : getErrorData() , getPage() ,
                       getRequest() ,
                       getResponse() ,
                       getServletConfig() ,
                       getServletContext() ,
                       getSession() ,
                       getAttribute() ,
                   getAttributeNamesInScope() ,
                       getAttributesScope() ,
                      getExpression!Eval!uator() ,
                       getOut() ,
                       getVariableResolver()

 사용법 : ${기본객체.속성}
   ex) ${pageScope.arr[0]} , ${param.valueName} , ${pageContext.request.method}
- 활성/비활성화 : <% page isELignored="true" %> -> true : 비활성, false : 활성

---------------------------------------------------------------

JSTL (Jsp Standard Tag Library)
- jstl.jar와 standard.jar 파일을 톰캣(Tomcat) 폴더의 lib 폴더에 복사 후 사용
- 속성 : set , remove , if , choose , forEach, forTokens , Import , redirect , url , catch , out
- 사용법 : <c:속성 속성에따른조건> </속성>
   ex)
<c:set var="변수명" value="${값}" />
<c:if test="${조건}">
<c:forEach begin="시작값" end="끝값" step="증가값" var="변수명" varStatus="접근값명">
<c:choose>
<c:when test="조건"> contents </c:when>
<c:otherwise> contents </c:otherwise>
</c:choose>
</c:forEach>
</c:if>
<c:forTokens var="변수명" items="문자열" delims="구분자"> contests </c:forTokens>
※ forEach 문에서 step은 기본 1증가, 접근값의 index와 count 추출 가능

* forEach문의 row 정보를 확인하기 위하여 사용하는 varStatus 의 속성
속성 : current , index , count , first ,
          last , begin , end , step 등이 있다.
사용법 : ${접근값명.get속성명()} , ${접근값명.속성명}