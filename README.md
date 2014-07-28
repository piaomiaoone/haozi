haozi
=====

测试
var getToken = function(callback, token) {
    $.ajax({
        onsuccess: function(data) {
            callback(data.id, token);
        }
    });
};

var token = 1;
var isLoading = false;


var requestList = function() {
    if (isLoading) {
        return null;
    }
    isLoading = true;
    token++;

    function onsuccess(id, requestToken) {
        $.ajax({
            data: {
                id: id
            },
            onsuccess: function(string) {
                if (requestToken == token) {
                    renderList(string);
                }
