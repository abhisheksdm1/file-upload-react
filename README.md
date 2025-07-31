```

import React, { useState, useRef } from "react";

function Test1() {
  const [image, setImage] = useState(null);
  const fileInputRef = useRef(null);

  const handleImageChange = (e) => {
    const file = e.target.files[0];
    if (file && file.type.startsWith("image/")) {
      const imageUrl = URL.createObjectURL(file);
      setImage(imageUrl);
    }
  };

  const handleRemoveImage = () => {
    setImage(null);
    if (fileInputRef.current) {
      fileInputRef.current.value = null; // clear the input value
    }
  };

  return (
    <div className="p-4">
      {/* {!image && ( */}
      <input
        type="file"
        accept="image/*"
        id="myfile"
        name="myfile"
        onChange={handleImageChange}
        ref={fileInputRef}
      />
      {/* )} */}

      {/* {image && ( */}
      <div className="mt-4 relative w-fit">
        <img
          src={image}
          alt="Preview"
          className="w-64 h-64 object-cover rounded shadow"
        />
        <button
          onClick={handleRemoveImage}
          className="absolute top-1 right-1 bg-red-500 text-white rounded-full p-1 hover:bg-red-600"
        >
          ✕
        </button>
      </div>
      {/* )} */}
    </div>
  );
}

export default Test1;
```
