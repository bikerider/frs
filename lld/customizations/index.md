<span id="_Toc449374820" class="anchor"><span id="_Toc460322563" class="anchor"></span></span>Revision History {#revision-history .TTULOGLOSARIO}
==============================================================================================================

  Release version   Document version   Date         Description
  ----------------- ------------------ ------------ ----------------------------------------------------------
  R2.0.0            v0.0               30/09/2016   Initial version (based on gConnectOB\_R1.2.8\_v1.6.docx)
                                                    
                                                    
                                                    
                                                    
                                                    
                                                    
                                                    

<span id="_Ref364077861" class="anchor"><span id="_Toc449442456" class="anchor"><span id="_Toc460322564" class="anchor"></span></span></span>Introduction {#introduction .TTULOCAP}
=========================================================================================================================================================

<span id="_Toc460251504" class="anchor"><span id="_Toc460322565" class="anchor"></span></span>Scope {#scope .Chaptertitle1}
---------------------------------------------------------------------------------------------------

This documents provides the gConnectOB Customizations per country.
gConnectOB High level design and Low Level Design specification can be
found at \[1\] and \[2\].

<span id="_Toc454212467" class="anchor"><span id="_Toc460322566" class="anchor"></span></span>UK Normalization Service behaviour {#uk-normalization-service-behaviour .CHAPTERTITLE}
================================================================================================================================

Following examples present normalization service logic in UK:

  Input           Input Nature of Address            Requested Output Nature of Address   Result (Number+NAI)
  --------------- ---------------------------------- ------------------------------------ ---------------------
  8876            Unknown or local/subscriber type   Any                                  8876+NAC
  0666555777      Unknown or local/subscriber type   Local                                0666555777+NAC
  0666777888      Unknown or local/subscriber type   International                        0044666777888+INT
  666777888       Unknown type                       International                        666777888+NAC
  666777888       Local/subscriber type              International                        0044666777888+INT
  666777888       Unknown type                       Local                                666777888+NAC
  666777888       Local/subscriber type              Local                                0666777888+NAC
  +44666555777    Unknown or International type      Local                                0666555777+NAC
  +44666555777    Unknown or International type      International                        0044666555777+INT
  0044666555777   Unknown or International type      Local                                0666555777+NAC
  0044666555777   Unknown or International type      International                        0044666555777+INT
  44666555777     International type                 Local                                0666555777+NAC
  44666555777     International type                 International                        0044666555777+INT
  44666555777     Unknown                            Local                                44666555777+NAC
  44666555777     Unknown                            International                        44666555777+NAC
  +34555666777    Unknown or International type      Local                                003455566677+INT
  +34555666777    Unknown or International type      International                        003455566677+INT
  0034555666777   Unknown or International type      Local                                0034555666777+INT
  0034555666777   Unknown or International type      International                        0034555666777+INT
  34555666777     International type                 Local                                0034555666777+INT
  34555666777     Unknown type.                      Local                                34555666777+NAC
  34555666777     International type                 International                        0034555666777+INT
  34555666777     Unknown type.                      International                        34555666777+NAC

In case of input number has “unknown” nature of address, the number must
begin with “0”, “00”, “+” or be a short number. Otherwise the number
remains untouched as local or international.

<span id="_Toc454212468" class="anchor"><span id="_Toc460322567" class="anchor"></span></span>ARG Normalization Service behaviour {#arg-normalization-service-behaviour .CHAPTERTITLE}
=================================================================================================================================

The following table shows the dialing formats in Argentina:

![](./media/image7.jpeg){width="4.052083333333333in"
height="2.6666666666666665in"}

Where “CA” is the area code and “NL” is the local number. The following
examples present normalization service logic in Argentina according to
the table above:

  Input                Input Nature of Address   Requested Output Nature of Address   Result (Number+NAI)
  -------------------- ------------------------- ------------------------------------ -------------------------
  0111544724285\#123   Unknown                   International                        00541144724285\#123+INT
  \*13013              Unknown                   International                        \*13013+NAC
  00541144724285       Unknown                   International                        00541144724285+INT
  +541144724285        Unknown                   International                        00541144724285+INT
  0034666777888        Unknown                   International                        0034666777888+INT
  +34666777888         Unknown                   International                        0034666777888+INT
  005491144724285      Unknown                   International                        00541144724285+INT
  +5491144724285       Unknown                   International                        00541144724285+INT
  0111544724285        Unknown                   International                        00541144724285+INT
  01144724285          Unknown                   International                        00541144724285+INT
  0600111222333        Unknown                   International                        0600111222333+NAC
  1544724285           Unknown                   International                        005422144724285+INT
  541144724285         Unknown                   International                        00541144724285+INT
  5491144724285        Unknown                   International                        00541144724285+INT
  111544724285         Unknown                   International                        00541144724285+INT
  1144724285           Unknown                   International                        00541144724285+INT
  44724285             Unknown                   International                        005422144724285+INT
  34666777888          Unknown                   International                        34666777888+NAC
  6666                 Unknown                   International                        6666+NAC
  541144724285\#123    International             International                        00541144724285\#123+INT
  541144724285         International             International                        00541144724285+INT
  5491144724285        International             International                        00541144724285+INT
  34666777888          International             International                        0034666777888+INT
  01144724285\#123     National                  International                        00541144724285\#123+INT
  \*13013              National                  International                        \*13013+NAC
  0111544724285        National                  International                        00541144724285+INT
  01144724285          National                  International                        00541144724285+INT
  0600111222333        National                  International                        0600111222333+NAC
  1544724285           National                  International                        005422144724285+INT
  111544724285         National                  International                        00541144724285+INT
  1144724285           National                  International                        00541144724285+INT
  44724285             National                  International                        005422144724285+INT
  6666                 National                  International                        6666+NAC
  0111544724285\#123   Unknown                   National                             1144724285\#123+NAC
  \*13013              Unknown                   National                             \*13013+NAC
  00541144724285       Unknown                   National                             1144724285+NAC
  +541144724285        Unknown                   National                             1144724285+NAC
  005491144724285      Unknown                   National                             1144724285+NAC
  +5491144724285       Unknown                   National                             1144724285+NAC
  0034666777888        Unknown                   National                             0034666777888+INT
  +34666777888         Unknown                   National                             0034666777888+INT
  0111544724285        Unknown                   National                             1144724285+NAC
  01144724285          Unknown                   National                             1144724285+NAC
  0600111222333        Unknown                   National                             0600111222333+NAC
  1544724285           Unknown                   National                             22144724285+NAC
  541144724285         Unknown                   National                             1144724285+NAC
  5491144724285        Unknown                   National                             1144724285+NAC
  111544724285         Unknown                   National                             1144724285+NAC
  1144724285           Unknown                   National                             1144724285+NAC
  44724285             Unknown                   National                             22144724285+NAC
  34666777888          Unknown                   National                             34666777888+NAC
  6666                 Unknown                   National                             6666+NAC
  0111544724285\#123   National                  National                             1144724285\#123+NAC
  \*13013              National                  National                             \*13013+NAC
  0111544724285        National                  National                             1144724285+NAC
  01144724285          National                  National                             1144724285+NAC
  0600111222333        National                  National                             0600111222333+NAC
  1544724285           National                  National                             22144724285+NAC
  111544724285         National                  National                             1144724285+NAC
  1144724285           National                  National                             1144724285+NAC
  44724285             National                  National                             22144724285+NAC
  6666                 National                  National                             6666+NAC
  541144724285\#123    International             National                             1144724285\#123+NAC
  541144724285         International             National                             1144724285+NAC
  5491144724285        International             National                             1144724285+NAC
  34666777888          International             National                             0034666777888+INT

In some cases included in the table above the area code “221” has been
added as an example (“221” is supposed to be the area code of the other
user when a number without area code is normalized).

<span id="_Toc258852268" class="anchor"><span id="_Toc454212469" class="anchor"><span id="_Toc460322568" class="anchor"></span></span></span>PER Normalization Service behaviour {#per-normalization-service-behaviour .CHAPTERTITLE}
================================================================================================================================================================================

B numbers received from network (terminating scenarios) or App
(originating scenarios):

  > Dialing case               > B format            > International normalization (Number+NAI)   > National normalization (Number+NAI)
  ---------------------------- --------------------- -------------------------------------------- ---------------------------------------
  > Basic dialings
  > Mobile-&gt;Fixed (Orig)    0+1XXXXXXX            00+51+1XXXXXXX+INT                           > 0+1XXXXXXX+NAC
  > Mobile-&gt;Fixed (Orig)    0+XXXXXXXX            00+51+XXXXXXXX+INT                           > 0+XXXXXXXX+NAC
  > Mobile-&gt;Fixed (Orig)    “+”+51+1XXXXXXX       00+51+1XXXXXXX+INT                           > 0+1XXXXXXX+NAC
  > Mobile-&gt;Fixed (Orig)    “+”+51+XXXXXXXX       00+51+XXXXXXXX+INT                           > 0+XXXXXXXX+NAC
  > Mobile-&gt;Fixed (Orig)    00+51+1XXXXXXX        00+51+1XXXXXXX+INT                           > 0+1XXXXXXX+NAC
  > Mobile-&gt;Fixed (Orig)    00+51+XXXXXXXX        00+51+XXXXXXXX+INT                           > 0+XXXXXXXX+NAC
  > Mobile-&gt;Fixed (Orig)    “+”+CC(!51) +NSN      00+CC+NSN+INT                                > 00+CC+NSN+INT
  > Mobile-&gt;Fixed (Orig)    00+CC(!51)+NSN        00+CC+NSN+INT                                > 00+CC+NSN+INT
  > Mobile-&gt;Fixed (Orig)    19XX+00+CC+NSN        19XX+00+CC+NSN+NAC                           > 19XX+00+CC+NSN+NAC
  > Mobile-&gt;Mobile (Orig)   9XXXXXXXX             00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile (Orig)   “+”+51+9XXXXXXXX      00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile (Orig)   00+51+9XXXXXXXX       00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile (Orig)   “+”+CC(!51)+NSN       00+CC+NSN+INT                                > 00+CC+NSN+INT
  > Mobile-&gt;Mobile (Orig)   00+CC(!51)+NSN        00+CC+NSN+INT                                > 00+CC+NSN+INT
  > Mobile-&gt;Mobile (Orig)   19XX+00+CC+NSN        00+CC+NSN+NAC                                > 19XX+00+CC+NSN+NAC
  > Mobile-&gt;Mobile (Term)   9XXXXXXXX             00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile (Term)   “+”+51+9XXXXXXXX      00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile (Term)   00+51+9XXXXXXXX       00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile (Term)   51+9XXXXXXXX          00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Fixed-&gt;Mobile (Term)    9XXXXXXXX             00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Fixed-&gt;Mobile (Term)    “+”+51+9XXXXXXXX      00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Fixed-&gt;Mobile (Term)    00+51+9XXXXXXXX       00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  > Fixed-&gt;Mobile (Term)    51+9XXXXXXXX          00+51+9XXXXXXXX+INT                          > 9XXXXXXXX+NAC
  RI
  > Mobile-&gt;Service         0+80X+XXXXX           00+51+80X+XXXXX+INT                          > 0+80XXXXXX+NAC
  Svc Especiales (\*)
  > Mobile-&gt;Service         1YX                   1YX+NAC                                      > 1YX+NAC
  > Mobile-&gt;Service         1YXX                  1YXX+NAC                                     > 1YXX+NAC
  > Mobile-&gt;Service         “\*”+VariableLength   “\*”+VariableLength+NAC                      > “\*”+VariableLength+NAC
  > Mobile-&gt;Service         “\#”+VariableLength   “\#”+VariableLength+NAC                      > “\#”+VariableLength+NAC
  > Mobile-&gt;Service         19XX+1YX              1YX+NAC                                      > 19XX+1YX+NAC
  > Mobile-&gt;Service         19XX+1YXX             1YXX+NAC                                     > 19XX+1YXX+NAC
  > Suplementarios?                                                                               
  > Mobile-&gt;Service         “\*”+VariableLength   “\*”+VariableLength+NAC                      > “\*”+VariableLength+NAC
  > Mobile-&gt;Service         “\#”+VariableLength   “\#”+VariableLength+NAC                      > “\#”+VariableLength+NAC
  RPM
  > Mobile-&gt;RPM             “\*” ó “\#”+XXXXXX    “\*” ó “\#”+XXXXXX+NAC                       “\*” ó “\#”+XXXXXX+NAC
  > Mobile-&gt;RPM             “\*” ó “\#”+XXXXXXX   “\*” ó “\#”+XXXXXXX+NAC                      “\*” ó “\#”+XXXXXXX+NAC
  > Mobile-&gt;RPM             “\*”ó “\#”+XXXXXXXX   “\*” ó “\#”+XXXXXXXX+NAC                     “\*” ó “\#”+XXXXXXXX+NAC
  > Mobile-&gt;RPM             \#9+XXXXXXXX          \#9+XXXXXXXX+NAC                             \#9+XXXXXXXX+NAC
  > Mobile-&gt;RPM             \#0+XXXXXXXX          \#0+XXXXXXXX+NAC                             \#0+XXXXXXXX+NAC

(\*) Y from 0 to 5, X from 0 to 9

A number format received in app originated scenarios:

  > Dialing case    > A format         > International normalization   > National normalization
  ----------------- ------------------ ------------------------------- --------------------------
  > App -&gt; Any   00+51+9XXXXXXXX    00+51+9XXXXXXXX+INT             > 9XXXXXXXX+NAC
  > App -&gt; Any   “+”+51+9XXXXXXXX   00+51+9XXXXXXXX+INT             > 9XXXXXXXX+NAC
  > App -&gt; Any   51+9XXXXXXXX       00+51+9XXXXXXXX+INT             > 9XXXXXXXX+NAC

A number format in terminating scenarios

  > Dialing case         > B format         > International normalization   > National normalization
  ---------------------- ------------------ ------------------------------- --------------------------
  > Mobile-&gt;Mobile    9XXXXXXXX          00+51+9XXXXXXXX+INT             > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile    “+”+51+9XXXXXXXX   00+51+9XXXXXXXX+INT             > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile    00+51+9XXXXXXXX    00+51+9XXXXXXXX+INT             > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile    51+9XXXXXXXX       00+51+9XXXXXXXX+INT             > 9XXXXXXXX+NAC
  > Mobile-&gt;Mobile    “+”+CC+NSN         00+CC+NSN+INT                   00+CC+NSN+INT
  > Mobile-&gt;Mobile    00+CC+NSN          00+CC+NSN+INT                   00+CC+NSN+INT
  > Mobile-&gt;Mobile    CC+NSN             00+CC+NSN+INT                   00+CC+NSN+INT
  > Fixed -&gt; Mobile   0+1XXXXXXX         00+51+1XXXXXXX+INT              0+1XXXXXXX+NAC
  > Fixed -&gt; Mobile   0+XX+XXXXXX        00+51+XX+XXXXXX+INT             0+XX+XXXXXX+NAC
  > Fixed -&gt; Mobile   1XXXXXXX           00+51+1XXXXXXX+INT              0+1XXXXXXX+NAC
  > Fixed -&gt; Mobile   XX+XXXXXX          00+51+XX+XXXXXX+INT             0+XX+XXXXXX+NAC
  > Fixed -&gt; Mobile   “+”+51+XXXXXXXX    00+51+1XXXXXXX+INT              0+1XXXXXXX+NAC
  > Fixed -&gt; Mobile   00+51+XXXXXXXX     00+51+XX+XXXXXX+INT             0+XX+XXXXXX+NAC
  > Fixed -&gt; Mobile   51+XXXXXXXX        00+51+XX+XXXXXX+INT             0+XX+XXXXXX+NAC
  > Fixed -&gt; Mobile   “+”+CC(!51)+NSN    00+CC+NSN+INT                   00+CC+NSN+INT
  > Fixed -&gt; Mobile   00+CC(!51)+NSN     00+CC+NSN+INT                   00+CC+NSN+INT
  > Fixed -&gt; Mobile   CC+NSN             00+CC+NSN+INT                   00+CC+NSN+INT

<span id="_Toc454212470" class="anchor"><span id="_Toc460322569" class="anchor"></span></span>COL Normalization Service behaviour {#col-normalization-service-behaviour .CHAPTERTITLE}
=================================================================================================================================

Following examples present normalization service logic in Colombia **for
calls**:

  Input                Input Nature of Address   Requested Output Nature of Address   Result (Number+NAI)
  -------------------- ------------------------- ------------------------------------ ------------------------
  +570312345678        Unknown                   International                        009570312345678+NAC
  00957312345678       Unknown                   International                        00957312345678+NAC
  0388765432           Unknown                   International                        005788765432+INT
  0312345              Unknown                   International                        0312345+NAC
  3123456789           Unknown                   International                        00573123456789+INT
  312345678            Unknown                   International                        0057312345678+NAC
  00573580000011C123   Unknown                   International                        00573580000011C123+NAC
  0388765432           National                  International                        005788765432+INT
  038876543211         National                  International                        00578876543211+INT
  038876543            National                  International                        038876543+NAC
  3123123123           National                  International                        00573123123123+INT
  312312312            National                  International                        312312312+NAC
  123456789            National                  International                        123456789+NAC
  +570312345678        International             International                        00570312345678+INT
  00570312345678       International             International                        00570312345678+INT
  570312345678         International             International                        00570312345678+INT
  +570312345678        Unknown                   National                             009570312345678+NAC
  570312345678         Unknown                   National                             570312345678+NAC
  038876543211         National                  National                             8876543211+NAC
  0388765432           National                  National                             0388765432+NAC
  123456789            National                  National                             123456789+NAC
  +570312345678        International             National                             570312345678+NAC
  00570312345678       International             National                             570312345678+NAC
  5711234567           International             National                             0311234567+NAC
  5731234567           International             National                             31234567+NAC
  34666666666          International             National                             0034666666666+NAC

Following examples present normalization service logic in Colombia **for
messaging**:

  Input                Input Nature of Address   Requested Output Nature of Address   Result (Number+NAI)
  -------------------- ------------------------- ------------------------------------ ------------------------
  +570312345678        Unknown                   International                        00570312345678+INT
  00957312345678       Unknown                   International                        0057312345678+INT
  0388765432           Unknown                   International                        005788765432+INT
  0312345              Unknown                   International                        0312345+NAC
  3123456789           Unknown                   International                        00573123456789+INT
  312345678            Unknown                   International                        0057312345678+NAC
  00573580000011C123   Unknown                   International                        00573580000011C123+NAC
  0388765432           National                  International                        005788765432+INT
  038876543211         National                  International                        00578876543211+INT
  038876543            National                  International                        038876543+NAC
  3123123123           National                  International                        00573123123123+INT
  312312312            National                  International                        312312312+NAC
  123456789            National                  International                        123456789+NAC
  +570312345678        International             International                        00570312345678+INT
  00570312345678       International             International                        00570312345678+INT
  570312345678         International             International                        00570312345678+INT
  0095711234567        Unknown                   National                             0311234567+NAC
  009571123456         Unknown                   National                             1123456+NAC
  00958123456789       Unknown                   National                             0058123456789+INT
  +5711234567          Unknown                   National                             0311234567+NAC
  +5731234567          Unknown                   National                             31234567+NAC
  +34666777888         Unknown                   National                             0034666777888+INT
  570312345678         Unknown                   National                             570312345678+NAC
  038876543211         National                  National                             8876543211+NAC
  0388765432           National                  National                             0388765432+NAC
  123456789            National                  National                             123456789+NAC
  +570312345678        International             National                             570312345678+NAC
  00570312345678       International             National                             570312345678+NAC
  5711234567           International             National                             0311234567+NAC
  5731234567           International             National                             31234567+NAC
  34666666666          International             National                             0034666666666+NAC

<span id="_Toc454212471" class="anchor"><span id="_Toc460322570" class="anchor"></span></span>BRA Normalization Service behaviour {#bra-normalization-service-behaviour .CHAPTERTITLE}
=================================================================================================================================

Following examples present normalization service logic in Brazil **for
calls**:

  Input             Input Nature of Address   Requested Output Nature of Address   Result (Number+NAI)
  ----------------- ------------------------- ------------------------------------ ---------------------
  1234              Unknown                   International                        1234+NAC
  +1534666666666    Unknown                   International                        001534666666666+NAC
  001534666666666   Unknown                   International                        001534666666666+NAC
  90901234567       Unknown                   International                        90901234567+NAC
  800123456         Unknown                   International                        800123456+NAC
  0123456789        Unknown                   International                        0123456789+NAC
  123456789         Unknown                   International                        005421123456789+INT
  1123456789        Unknown                   International                        1123456789+NAC
  111123456789      Unknown                   International                        111123456789+NAC
  1234              Unknown                   National                             1234+NAC
  +1534666666666    Unknown                   National                             001534666666666+NAC
  001534666666666   Unknown                   National                             001534666666666+NAC
  90901234567       Unknown                   National                             90901234567+NAC
  800123456         Unknown                   National                             800123456+NAC
  0123456789        Unknown                   National                             0123456789+NAC
  123456789         Unknown                   National                             21123456789+NAC
  111123456789      Unknown                   National                             111123456789+NAC
  +1534666666666    International             National                             001534666666666+NAC
  001534666666666   International             National                             001534666666666+NAC
  +5534666666666    International             National                             34666666666+NAC
  005534666666666   International             National                             34666666666+NAC
  +5434666666666    International             National                             005434666666666+INT
  005434666666666   International             National                             005434666666666+INT
  +1534666666666    International             International                        001534666666666+INT
  001534666666666   International             International                        001534666666666+INT
  +5534666666666    International             International                        005534666666666+INT
  005534666666666   International             International                        005534666666666+INT
  +5434666666666    International             International                        005434666666666+INT
  005434666666666   International             International                        005434666666666+INT
  55111111111       International             International                        0055111111111+INT
  56123456789       International             International                        0056123456789+INT
  1234              National                  International                        1234+NAC
  800123            National                  International                        800123+NAC
  0123456789        National                  International                        0123456789+NAC
  12345678          National                  International                        0055123456789+INT
  1234567899        National                  International                        00551234567899+INT
  123123123123      National                  International                        123123123123+NAC
  1234              National                  National                             1234+NAC
  901234567         National                  National                             901234567+NAC
  800123456         National                  National                             800123456+NAC
  080011223344      National                  National                             080011223344+NAC
  99887766          National                  National                             2199887766+NAC
  111222333444      National                  National                             111222333444+NAC

Following examples present normalization service logic in Brazil **for
messages**:

  Input              Input Nature of Address   Requested Output Nature of Address   Result (Number+NAI)
  ------------------ ------------------------- ------------------------------------ ---------------------
  1234               Unknown                   International                        1234+NAC
  +15551234567899    Unknown                   International                        00551234567899+INT
  0015551234567899   Unknown                   International                        00551234567899+INT
  001534666666666    Unknown                   International                        001534666666666+INT
  90901234567        Unknown                   International                        90901234567+NAC
  800123456          Unknown                   International                        800123456+NAC
  0151234567899      Unknown                   International                        00551234567899+INT
  01234567899        Unknown                   International                        00551234567899+INT
  123456789          Unknown                   International                        0055123456789+INT
  111222333444       Unknown                   International                        111222333444+NAC
  1234               Unknown                   National                             1234+NAC
  +1534666666666     Unknown                   National                             001534666666666+NAC
  001534666666666    Unknown                   National                             001534666666666+NAC
  90901234567        Unknown                   National                             90901234567+NAC
  800123456          Unknown                   National                             800123456+NAC
  0123456789         Unknown                   National                             0123456789+NAC
  123456789          Unknown                   National                             21123456789+NAC
  111123456789       Unknown                   National                             111123456789+NAC
  +1534666666666     International             International                        001534666666666+INT
  001534666666666    International             International                        001534666666666+INT
  55111111111        International             International                        0055111111111+INT
  56123456789        International             International                        0056123456789+INT
  +1534666666666     International             National                             001534666666666+NAC
  001534666666666    International             National                             001534666666666+NAC
  +5534666666666     International             National                             34666666666+NAC
  005534666666666    International             National                             34666666666+NAC
  +5434666666666     International             National                             005434666666666+INT
  005434666666666    International             National                             005434666666666+INT
  1234               National                  International                        1234+NAC
  800123             National                  International                        800123+NAC
  0123456789         National                  International                        0123456789+NAC
  12345678           National                  International                        0055123456789+INT
  1234567899         National                  International                        00551234567899+INT
  123123123123       National                  International                        123123123123+NAC
  1234               National                  National                             1234+NAC
  800123456          National                  National                             800123456+NAC
  080011223344       National                  National                             080011223344+NAC
  99887766           National                  National                             2199887766+NAC
  111222333444       National                  National                             111222333444+NAC

<span id="_Toc454212472" class="anchor"><span id="_Toc460322571" class="anchor"></span></span>MX Normalization Service behaviour (UNIVERSAL) {#mx-normalization-service-behaviour-universal .CHAPTERTITLE}
============================================================================================================================================

Following examples present normalization service logic in Mexico:

  Input               Input Nature of Address   Requested Output Nature of Address   Result (Number + NAI)
  ------------------- ------------------------- ------------------------------------ -----------------------
  005215512345678     Unknown                   International                        00525512345678+INT
  +5215512345678      Unknown                   International                        00525512345678+INT
  00520335512345678   Unknown                   International                        00520335512345678+INT
  +520335512345678    Unknown                   International                        00520335512345678+INT
  +5201512345678      Unknown                   International                        00525512345678+INT
  +52044512345678     Unknown                   International                        00525512345678+INT
  +52045512345678     Unknown                   International                        00525512345678+INT
  00525512345678      Unknown                   International                        00525512345678+INT
  +525512345678       Unknown                   International                        00525512345678+INT
  +447720322322       Unknown                   International                        00447720322322+INT
  0335512345678       Unknown                   International                        00520335512345678+INT
  015512345678        Unknown                   International                        00525512345678+INT
  0445512345678       Unknown                   International                        00525512345678+INT
  0455512345678       Unknown                   International                        00525512345678+INT
  5512345678          Unknown                   International                        00525512345678+INT
  112                 Unknown                   International                        112+NAC
  0XX                 Unknown                   International                        0XX+NAC
  \*100               Unknown                   International                        \*100+NAC
  \#100\#             Unknown                   International                        \#100\#+NAC
  015512345678        National                  International                        00525512345678+INT
  0445512345678       National                  International                        00525512345678+INT
  0455512345678       National                  International                        00525512345678+INT
  0335512345678       National                  International                        00520335512345678+INT
  5512345678          National                  International                        00521234567890+INT
  112                 National                  International                        112+NAC
  0XX                 National                  International                        0XX+NAC
  \*100               National                  International                        \*100+NAC
  \#100\#             National                  International                        \#100\#+NAC
  005215512345678     International             International                        00525512345678+INT
  +5215512345678      International             International                        00525512345678+INT
  0052015512345678    International             International                        00525512345678+INT
  +52015512345678     International             International                        00525512345678+INT
  00520445512345678   International             International                        00525512345678+INT
  +520445512345678    International             International                        00525512345678+INT
  00520455512345678   International             International                        00525512345678+INT
  +520455512345678    International             International                        00525512345678+INT
  00520335512345678   International             International                        00520335512345678+INT
  +520335512345678    International             International                        00520335512345678+INT
  00525512345678      International             International                        0052512345678+INT
  +525512345678       International             International                        0052512345678+INT
  5215512345678       International             International                        00525512345678+INT
  52015512345678      International             International                        00525512345678+INT
  520445512345678     International             International                        00525512345678+INT
  520455512345678     International             International                        00525512345678+INT
  520335512345678     International             International                        00520335512345678+INT
  525512345678        International             International                        0052512345678+INT
  44720322322         International             International                        00447720322322+INT
  005215512345678     Unknown                   National                             5512345678+NAC
  +5215512345678      Unknown                   National                             5512345678+NAC
  00520335512345678   Unknown                   National                             0335512345678+NAC
  +520335512345678    Unknown                   National                             0335512345678+NAC
  +5201512345678      Unknown                   National                             5512345678+NAC
  +52044512345678     Unknown                   National                             5512345678+NAC
  +52045512345678     Unknown                   National                             5512345678+NAC
  00525512345678      Unknown                   National                             5512345678+NAC
  +525512345678       Unknown                   National                             5512345678+NAC
  +447720322322       Unknown                   National                             00447720322322+INT
  0335512345678       Unknown                   National                             0335512345678+NAC
  015512345678        Unknown                   National                             5512345678+NAC
  0445512345678       Unknown                   National                             5512345678+NAC
  0455512345678       Unknown                   National                             5512345678+NAC
  5512345678          Unknown                   National                             5512345678+NAC
  112                 Unknown                   National                             112+NAC
  0XX                 Unknown                   National                             0XX+NAC
  \*100               Unknown                   National                             \*100+NAC
  \#100\#             Unknown                   National                             \#100\#+NAC
  015512345678        National                  National                             5512345678+NAC
  0445512345678       National                  National                             5512345678+NAC
  0455512345678       National                  National                             5512345678+NAC
  0335512345678       National                  National                             0335512345678+NAC
  5512345678          National                  National                             5512345678+NAC
  112                 National                  National                             112+NAC
  0XX                 National                  National                             0XX+NAC
  \*100               National                  National                             \*100+NAC
  \#100\#             National                  National                             \#100\#+NAC
  005215512345678     International             National                             5512345678+NAC
  +5215512345678      International             National                             5512345678+NAC
  0052015512345678    International             National                             5512345678+NAC
  +52015512345678     International             National                             5512345678+NAC
  00520445512345678   International             National                             5512345678+NAC
  +520445512345678    International             National                             5512345678+NAC
  00520455512345678   International             National                             5512345678+NAC
  +520455512345678    International             National                             5512345678+NAC
  00520335512345678   International             National                             0335512345678+NAC
  +520335512345678    International             National                             0335512345678+NAC
  00525512345678      International             National                             5512345678+NAC
  +525512345678       International             National                             5512345678+NAC
  5215512345678       International             National                             5512345678+NAC
  52015512345678      International             National                             5512345678+NAC
  520445512345678     International             National                             5512345678+NAC
  520455512345678     International             National                             5512345678+NAC
  520335512345678     International             National                             0335512345678+NAC
  525512345678        International             National                             5512345678+NAC
  44720322322         International             National                             00447720322322+INT

Mexico normalization is based on gConnectOB Universal normalization
component, a configuration example is included in the table below:

                    Input NAI   Input Expression                          Output NAI   Output Format   Common
  ----------------- ----------- ----------------------------------------- ------------ --------------- --------
  ToInternational   UNKWN       (\\+|00)521(\[1-9\])(\\d{9})              INT          0052(2)(3)      
                    UNKWN       (\\+|00)52(01|044|045)(\[1-9\])(\\d{9})   INT          0052(3)(4)      
                    UNKWN       (\\+|00)52(\\d{3})(\[1-9\])(\\d{9})       INT          0052(2)(3)(4)   
                    UNKWN       (\\+|00)52(\[1-9\])(\\d{9})               INT          0052(2)(3)      
                    UNKWN       (\\+|00)(.\*)                             INT          00(2)           
                    UNKWN       (01|044|045)(\[1-9\])(\\d{9})             INT          0052(2)(3)      
                    UNKWN       (\\d{3})(\[1-9\])(\\d{9})                 INT          0052(1)(2)(3)   
                    UNKWN       (\[1-9\])(\\d{9})                         INT          0052(1)(2)      
                    UNKWN       (.\*)                                     NAC          (1)             
                    NAC         (01|044|045)(\[1-9\])(\\d{9})             INT          0052(2)(3)      
                    NAC         (\\d{3})(\[1-9\])(\\d{9})                 INT          0052(1)(2)(3)   
                    NAC         (\[1-9\])(\\d{9})                         INT          0052(1)(2)      
                    NAC         (.\*)                                     NAC          (1)             
                    INT         (+|00)521(\[1-9\])(\\d{9})                INT          0052(2)(3)      
                    INT         (+|00)52(01|044|045)(\[1-9\])(\\d{9})     INT          0052(2)(3)      
                    INT         (+|00)52(\\d{3})(\[1-9\])(\\d{9})         INT          0052(2)(3)(4)   
                    INT         (+|00)52(\[1-9\])(\\d{9})                 INT          0052(1)(2)      
                    INT         521(\[1-9\])(\\d{9})                      INT          0052(1)(2)      
                    INT         52(01|044|045)(\[1-9\])(\\d{9})           INT          0052(2)(3)      
                    INT         52(\\d{3})(\[1-9\])(\\d{9})               INT          0052(1)(2)(3)   
                    INT         52(\[1-9\])(\\d{9})                       INT          0052(1)(2)      
                    INT         (.\*)                                     INT          00(1)           
  ToNational        UNKWN       (\\+|00)521(\[1-9\])(\\d{9})              NAC          (2)(3)          
                    UNKWN       (\\+|00)52(01|044|045)(\[1-9\])(\\d{9})   NAC          (3)(4)          
                    UNKWN       (\\+|00)52(\\d{3})(\[1-9\])(\\d{9})       NAC          (2)(3)(4)       
                    UNKWN       (\\+|00)52(\[1-9\])(\\d{9})               NAC          (2)(3)          
                    UNKWN       (\\+|00)(.\*)                             INT          00(2)           
                    UNKWN       (01|044|045)(\[1-9\])(\\d{9})             NAC          (2)(3)          
                    UNKWN       (\\d{3})(\[1-9\])(\\d{9})                 NAC          (1)(2)(3)       
                    UNKWN       (\[1-9\])(\\d{9})                         NAC          (1)(2)          
                    UNKWN       (.\*)                                     NAC          (1)             
                    NAC         (01|044|045)(\[1-9\])(\\d{9})             NAC          (2)(3)          
                    NAC         (\\d{3})(\[1-9\])(\\d{9})                 NAC          (1)(2)(3)       
                    NAC         (\[1-9\])(\\d{9})                         NAC          (1)(2)          
                    NAC         (.\*)                                     NAC          (1)             
                    INT         (+|00)521(\[1-9\])(\\d{9})                NAC          (2)(3)          
                    INT         (+|00)52(01|44|045)(\[1-9\])(\\d{9})      NAC          (2)(3)          
                    INT         (+|00)52(\\d{3})(\[1-9\])(\\d{9})         NAC          (2)(3)(4)       
                    INT         (+|00)52(\[1-9\])(\\d{9})                 NAC          (2)(3)          
                    INT         521(\[1-9\])(\\d{9})                      NAC          (1)(2)          
                    INT         52(01|044|045)(\[1-9\])(\\d{9})           NAC          (2)(3)          
                    INT         52(\\d{3})(\[1-9\])(\\d{9})               NAC          (1)(2)(3)       
                    INT         52(\[1-9\])(\\d{9})                       NAC          (1)(2)          

<span id="_Toc454212473" class="anchor"><span id="_Toc460322572" class="anchor"></span></span>CR Normalization Service behaviour (UNIVERSAL) {#cr-normalization-service-behaviour-universal .CHAPTERTITLE}
============================================================================================================================================

Following examples present normalization service logic in Costa Rica:

  Input            Input Nature of Address   Requested Output Nature of Address   Result (Number + NAI)
  ---------------- ------------------------- ------------------------------------ -----------------------
  +50666666666     Unknown                   International                        0050666666666+INT
  +447720322322    Unknown                   International                        00447720322322+INT
  0050666666666    Unknown                   International                        0050666666666+INT
  00447720322322   Unknown                   International                        00447720322322+INT
  66666666         Unknown                   International                        0050666666666+INT
  23771234         Unknown                   International                        0050623771234+INT
  8001234567       Unknown                   International                        005068001234567+INT
  112              Unknown                   International                        112+NAC
  1xxx             Unknown                   International                        1xxx+NAC
  \#31\#66666666   Unknown                   International                        \#31\#66666666+NAC
  12345678765      Unknown                   International                        12345678765+NAC
  66666666         National                  International                        0050666666666+INT
  23771234         National                  International                        0050623771234+INT
  112              National                  International                        112+NAC
  1XXX             National                  International                        1XXX+NAC
  8001234567       National                  International                        005068001234567+INT
  \#31\#66666666   National                  International                        \#31\#66666666+NAC
  12345678765      National                  International                        12345678765+NAC
  +50666666666     International             International                        0050666666666+INT
  +447720322322    International             International                        00447720322322+INT
  0050666666666    International             International                        0050666666666+INT
  00447720322322   International             International                        00447720322322+INT
  50666666666      International             International                        0050666666666+INT
  50623771234      International             International                        0050623771234+INT
  447720322322     International             International                        00447720322322+INT
  +50666666666     Unknown                   National                             66666666+NAC
  +447720322322    Unknown                   National                             00447720322322+INT
  0050666666666    Unknown                   National                             66666666+NAC
  00447720322322   Unknown                   National                             00447720322322+INT
  66666666         Unknown                   National                             66666666+NAC
  23771234         Unknown                   National                             23771234+NAC
  8001234567       Unknown                   National                             8001234567+NAC
  112              Unknown                   National                             112+NAC
  1xxx             Unknown                   National                             1xxx+NAC
  \#31\#66666666   Unknown                   National                             \#31\#66666666+NAC
  12345678765      Unknown                   National                             12345678765+NAC
  66666666         National                  National                             66666666+NAC
  23771234         National                  National                             23771234+NAC
  7891234          National                  National                             7891234+NAC
  112              National                  National                             112+NAC
  1XXX             National                  National                             1xxx+NAC
  8001234567       National                  National                             8001234567+NAC
  \#31\#66666666   National                  National                             \#31\#66666666+NAC
  12345678765      National                  National                             12345678765+NAC
  +50666666666     International             National                             66666666+NAC
  +447720322322    International             National                             00447720322322+INT
  0050666666666    International             National                             66666666+NAC
  00447720322322   International             National                             00447720322322+INT
  50666666666      International             National                             66666666+NAC
  50623771234      International             National                             23771234+NAC
  447720322322     International             National                             00447720322322+INT

Costa Rica normalization is based on gConnectOB Universal normalization
component, a configuration example is included in the table below:

                    Input NAI   Input Expression       Output NAI   Output Format   Common
  ----------------- ----------- ---------------------- ------------ --------------- --------
  ToInternational   UNKWN       (+|00)(.\*)            INT          00(2)           
                    UNKWN       (\[23456789\]\\d{7})   INT          00506(1)        
                    UNKWN       (800\\d{7})            INT          00506(1)        
                    UNKWN       (90\\d{8})             INT          00506(1)        
                    UNKWN       (.\*)                  NAC          (1)             
                    NAC         (\[23456789\]\\d{7})   INT          00506(1)        
                    NAC         (800\\d{7})            INT          00506(1)        
                    NAC         (90\\d{8})             INT          00506(1)        
                    NAC         (.\*)                  NAC          (1)             
                    NAC         (+|00)(.\*)            INT          00(2)           
                    INT         (.\*)                  INT          00(1)           
                    INT         (+|00)(.\*)            INT          00(2)           
  ToNational        UNKWN       (+|00)(506)(.\*)       NAC          (3)             
                    UNKWN       (+|00)(.\*)            INT          00(2)           
                    UNKWN       (.\*)                  NAC          (1)             
                    NAC         (.\*)                  NAC          (1)             
                    INT         (+|00)(506)(.\*)       NAC          (3)             
                    INT         (+|00)(.\*)            INT          00(2)           
                    INT         (506)(.\*)             NAC          (2)             
                    INT         (.\*)                  INT          00(1)           

<span id="_Toc454212474" class="anchor"><span id="_Toc460322573" class="anchor"></span></span>PAN Normalization Service behaviour (UNIVERSAL) {#pan-normalization-service-behaviour-universal .CHAPTERTITLE}
=============================================================================================================================================

Following examples present normalization service logic in Panamá:

  Input            Input Nature of Address   Requested Output Nature of Address   Result (Number + NAI)
  ---------------- ------------------------- ------------------------------------ -----------------------
  +50766666666     Unknown                   International                        0050766666666+INT
  +447720322322    Unknown                   International                        00447720322322+INT
  0050766666666    Unknown                   International                        0050766666666+INT
  00447720322322   Unknown                   International                        00447720322322+INT
  66666666         Unknown                   International                        0050766666666+INT
  3771234          Unknown                   International                        005073771234+INT
  7891234          Unknown                   International                        005077891234+INT
  105              Unknown                   International                        105+NAC
  \#31\#66666666   Unknown                   International                        \#31\#66666666+NAC
  12345678765      Unknown                   International                        12345678765+NAC
  66666666         National                  International                        0050766666666+INT
  3771234          National                  International                        005077891234+INT
  7891234          National                  International                        005073771234+INT
  105              National                  International                        105+NAC
  \#31\#66666666   National                  International                        \#31\#66666666+NAC
  12345678765      National                  International                        12345678765+NAC
  +50766666666     International             International                        0050766666666+INT
  +447720322322    International             International                        00447720322322+INT
  0050766666666    International             International                        0050766666666+INT
  00447720322322   International             International                        00447720322322+INT
  50766666666      International             International                        0050766666666+INT
  5073771234       International             International                        00**507**3771234+INT
  5077891234       International             International                        005077891234+INT
  447720322322     International             International                        00447720322322+INT
  +50766666666     Unknown                   National                             66666666+NAC
  +447720322322    Unknown                   National                             00447720322322+INT
  0050766666666    Unknown                   National                             66666666+NAC
  00447720322322   Unknown                   National                             00447720322322+INT
  66666666         Unknown                   National                             66666666+NAC
  3771234          Unknown                   National                             3771234+NAC
  7891234          Unknown                   National                             7891234+NAC
  105              Unknown                   National                             105+NAC
  \#31\#66666666   Unknown                   National                             \#31\#66666666+NAC
  12345678765      Unknown                   National                             12345678765+NAC
  66666666         National                  National                             66666666+NAC
  3771234          National                  National                             3771234+NAC
  7891234          National                  National                             7891234+NAC
  105              National                  National                             105+NAC
  1XXX             National                  National                             1xxx+NAC
  \#31\#66666666   National                  National                             \#31\#66666666+NAC
  12345678765      National                  National                             12345678765+NAC
  +50766666666     International             National                             66666666+NAC
  +447720322322    International             National                             00447720322322+INT
  0050766666666    International             National                             66666666+NAC
  00447720322322   International             National                             00447720322322+INT
  50766666666      International             National                             66666666+NAC
  50723771234      International             National                             23771234+NAC
  447720322322     International             National                             00447720322322+INT

Panamá normalization is based on gConnectOB Universal normalization
component, a configuration example is included in the table below:

                    Input NAI   Input Expression      Output NAI   Output Format   Common
  ----------------- ----------- --------------------- ------------ --------------- --------
  ToInternational   UNKWN       (+|00)(.\*)           INT          00(2)           
                    UNKWN       (6\\d{7})             INT          00507(1)        
                    UNKWN       (\[2345789\]\\d{6})   INT          00507(1)        
                    UNKWN       (.\*)                 NAC          (1)             
                    NAC         (6\\d{7})             INT          00507(1)        
                    NAC         (\[2345789\]\\d{6})   INT          00507(1)        
                    NAC         (.\*)                 NAC          (1)             
                    INT         (+|00)(.\*)           INT          00(2)           
                    INT         (.\*)                 INT          00(1)           
  ToNational        UNKWN       (+|00)(507)(.\*)      NAC          (3)             
                    UNKWN       (+|00)(.\*)           INT          00(2)           
                    UNKWN       (.\*)                 NAC          (1)             
                    NAC         (.\*)                 NAC          (1)             
                    INT         (+|00)(507)(.\*)      NAC          (3)             
                    INT         (+|00)(.\*)           INT          00(2)           
                    INT         (507)(.\*)            NAC          (2)             
                    INT         (.\*)                 INT          00(1)           

<span id="_Toc460252300" class="anchor"><span id="_Toc460322574" class="anchor"></span></span>References {#references .CHAPTERTITLE}
========================================================================================================

1.  <span id="_Ref460318621" class="anchor"><span id="_Ref460248129"
    > class="anchor"></span></span>gConnectOB High Level Design.

2.  <span id="_Ref460321598" class="anchor"></span>gConnectOB Low
    > Level Design.

3.  gConnectOB Flow Diagrams: FlowDiagrams\_gConnect\_R2.x.vsd.

4.  <span id="_Ref460316903" class="anchor"></span>gConnectOB APIs.

5.  <span id="_Ref460316868" class="anchor"></span>gConnectOB Scenarios.


