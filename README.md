
function json2html(data) {
    // Initialize the HTML with table and user data attribute
    let html = `<table data-user="shruthilayagudimela@gmail.com"><thead><tr>`;

    // Get all unique headers from the data array
    const headers = new Set();
    data.forEach(item => {
        Object.keys(item).forEach(key => headers.add(key));
    });

    // Add headers to the table
    headers.forEach(header => {
        html += `<th>${header}</th>`;
    });
    html += `</tr></thead><tbody>`;

    // Generate table rows for each object in the data array
    data.forEach(row => {
        html += `<tr>`;
        headers.forEach(header => {
            html += `<td>${row[header] || ''}</td>`; // Add empty cell if property is missing
        });
        html += `</tr>`;
    });

    html += `</tbody></table>`;
    return html;
}

// Example usage
const data = [
    { Name: "Alice", Age: 25 },
    { Name: "Bob", Age: 30 },
    { Name: "Charlie", Age: 35, Gender: "M" }
];

console.log(json2html(data)); 
