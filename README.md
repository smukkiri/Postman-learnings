Download the student jar file and run in desktop
create new collections and add request (we can run collections also)
Use get with http://localhost:8080/student/1 or http://localhost:8080/student/2 etc
use below codes for testing. refer body for data fetched and test results for results

//Store the response in Jresponse variable for further use
let Jresponse = pm.response.json();


//To verify response code is 200
pm.test("Verify that response code is 200", function() {
    pm.response.to.have.status(200);
});


//To Verify that ErrorCode, ErrorMsg, IsSuccessful, ResponseData values are appropriate 
pm.test("Verify that Errorcode, ErrorMsg, Issuccessfull, ResponseData values are appropriate", function() {
    pm.expect(Jresponse.firstname).to.not.equal(null);
    pm.expect(Jresponse.lastname).to.not.equal(null);
      pm.expect(Jresponse.email).to.not.equal(null);
});


//To Verify that City Code doesn't have null value in the response
pm.test("Verify that City Code doesn't have null value in the response", function(){
    pm.expect(Jresponse.cityCode).not.equal(null);
});


pm.test("Courses contains accounting", function(){
    pm.expect(Jresponse.courses).to.be.contains("Accounting");
      });

pm.test("Courses not contains accouning", function(){
    pm.expect(Jresponse.courses).to.be.not.contains("Accouning");
      });
      

